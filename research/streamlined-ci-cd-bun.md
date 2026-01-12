# Plan B: Streamlined CI/CD (Bun + Cloudflare)

## Purpose

A lightweight CI/CD setup optimized for speed and developer productivity while the stack is still evolving.

This plan focuses on:
- fast feedback on pull requests
- minimal “must-pass” quality gates
- easy deployment to Cloudflare (Pages / Workers) from `main`
- room to add testing + security tooling later (Sentry, scanners, etc.)

---

## Current / Likely Stack

- Runtime: **Bun**
- Frontend/app framework (probable): **TanStack Start**
- Backend (probable): **Convex**
- Deployment: **Cloudflare Pages and/or Cloudflare Workers**
- CI provider: **GitHub Actions**
- PR review automation: **CodeRabbit**

> Note: Docker can still be used for local dev or alternative deployment targets, but Cloudflare deployments typically do not require Docker images.

---

## High-Level Workflow

### Triggers
- **Pull Request → `main`**
  - Run fast quality checks
  - No deploy
- **Push/Merge → `main`**
  - Run the same quality checks
  - Deploy to Cloudflare (Pages/Workers)

---

## Pipeline Stages (Conceptual)

### 1) Setup
- Checkout repo
- Setup Bun runtime
- Install deps (`bun install`)
- Cache dependencies (to keep runs fast)

### 2) Quality Gates (fast, essential)
Run as separate jobs in parallel or as separate steps (depending on how simple you want it):
- **Lint**: ESLint
- **Format check**: Prettier (check mode, not write)
- **Type check**: TypeScript

> Testing is planned but not required initially. Add Vitest once the stack is finalized.

### 3) Deploy (main branch only)
If quality gates pass and the ref is `main`:
- Deploy to **Cloudflare Pages** and/or **Cloudflare Workers**
  - Pages: build + publish
  - Workers: build + deploy (via Wrangler)

---

## CodeRabbit in the Flow

CodeRabbit complements CI by:
- reviewing PR diffs automatically
- suggesting improvements and catching issues early
- helping keep PRs small and standards consistent

CI remains the source of truth for pass/fail checks; CodeRabbit is advisory + review automation.

---

## Required Secrets (Typical for Cloudflare)

Depending on whether you use Pages, Workers, or both:

### Cloudflare Workers (Wrangler)
- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID` (sometimes optional depending on setup)

### Cloudflare Pages
Common approaches:
- Use the official Pages GitHub integration (no secrets needed in Actions), OR
- Deploy via API/CLI (then token is required)

If deploying via Actions, you’ll typically use:
- `CLOUDFLARE_API_TOKEN`
- `CLOUDFLARE_ACCOUNT_ID`
- `CLOUDFLARE_PAGES_PROJECT_NAME` (if applicable)

> Exact requirements depend on how you deploy (native integration vs wrangler/pages action).

---

## File/Config Expectations

Typical files in this Plan B setup:

- `.github/workflows/ci-cd.yml`
  - single workflow: quality checks + conditional deploy
- ESLint / Prettier config
  - `.eslintrc.json` (or `eslint.config.*`)
  - `.prettierrc`
  - `.prettierignore`
- Optional (later):
  - `vitest.config.ts` for unit tests
  - security scanners (Snyk, Trivy, CodeQL, etc.)
  - Sentry integration + release tracking

---

## What “Done” Looks Like

### Pull Requests
- Fast checks run automatically
- Failures block merge (recommended)
- CodeRabbit provides review feedback

### Main Branch
- Same checks run
- Successful run deploys to Cloudflare
- Main always represents a deployable state

---

## Planned Enhancements (Later)

- **Testing**
  - Vitest unit tests
  - integration tests once architecture is stable
- **Observability**
  - Sentry for error tracking (and optionally performance monitoring)
- **Security**
  - dependency scanning
  - static analysis (CodeQL)
  - secret scanning / policy checks

---

## Notes / Open Decisions

Because the stack is still being refined, these decisions can be deferred:
- Pages vs Workers split (or both)
- how Convex is configured across preview/prod environments
- whether Docker is used only for local dev or removed entirely
- formal staging environments (preview deploys may cover this initially)
  
Relational Integrity vs. BaaS:
 - Still auditing if Convex's document-style state management can replace the "Heavy Truth" requirements of the previous RDS/Neon PostgreSQL architecture.
