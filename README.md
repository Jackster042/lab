# 🧪 The Laboratory

> "Align on outcomes, prototype quickly, and refine relentlessly."

This repository serves as my **Systems Research & Development (R&D) center**. It is a conceptual staging area where I document the architecture, infrastructure pivots, and engineering logic of my upcoming systems. I prioritize **Engineering Integrity** and **Pragmatic Design** over framework-driven hype, pushing source code only once a system's architectural foundation is validated.

---

### 🏗️ Active Research & Prototyping

# Project Plan: Edge-First Football Dashboard (Infrastructure-First)

## 1. Project Overview

A modern full-stack testbed utilizing **TanStack Start**, **Neon (Postgres)**, and **Cloudflare**. The goal is to demonstrate a high-performance "Edge" architecture using **Cloudflare Hyperdrive** to eliminate database latency bottlenecks and **CodeRabbit/GitHub Actions** for automated quality gates.

---

## 2. Phase 1: The "Plumbing" (CI/CD & Edge Bootstrap)

**Objective:** Establish a "Green Path" from local code to a live Edge environment.

### Tasks:

- [ ] **Project Initialization:**
  - Initialize TanStack Start using the `cloudflare-pages` adapter.
  - Set up `pnpm` workspace and basic project structure.
- [ ] **GitHub Actions Setup:**
  - `ci.yml`: Automated Linting, Type-checking (`tsc`), and Drizzle Schema validation.
  - `deploy.yml`: Integration with Cloudflare Pages for automated "Preview Deployments" on every Pull Request.
- [ ] **Code Quality Automation:**
  - Integrate **CodeRabbit** via GitHub Marketplace.
  - Configure `.coderabbit.yaml` to prioritize Edge-runtime compatibility reviews.
- [ ] **Observability Baseline:**
  - Initialize **Sentry** with the `@sentry/cloudflare` SDK to capture Edge Function errors.

**Deliverables:**

- A functional CI/CD pipeline.
- A "Hello World" TanStack Start app live on a `*.pages.dev` domain.
- Automated PR feedback loop active via CodeRabbit.

---

## 3. Phase 2: The Data Backbone (Neon & Hyperdrive)

**Objective:** Secure and accelerate the data layer using connection pooling at the edge.

### Tasks:

- [ ] **Database Provisioning:**
  - Setup **Neon** project and create `dev` and `prod` branches.
  - Configure **Drizzle ORM** with `drizzle-kit` for migrations.
- [ ] **Cloudflare Hyperdrive Configuration:**
  - Create a Hyperdrive instance via `wrangler hyperdrive create`.
  - Map the Neon connection string to Hyperdrive.
  - Update `wrangler.toml` to expose the Hyperdrive binding.
- [ ] **Schema Definition:**
  - Define initial Drizzle schemas: `leagues`, `teams`, and `matches`.
  - Create a "Connectivity Test" server function to verify Hyperdrive latency vs. direct connection.

**Deliverables:**

- Drizzle schema pushed to Neon.
- Hyperdrive binding active and accessible within TanStack Start server functions.
- Latency metrics visible in function logs.

---

## 4. Phase 3: Data Ingestion & Logic

**Objective:** Populate the infrastructure with real-world European football data.

### Tasks:

- [ ] **API Integration:**
  - Securely store Football API keys in Cloudflare Secrets.
  - Implement a CRON trigger (Cloudflare Workers) or a manual sync script to fetch data from the API (e.g., API-Football).
- [ ] **Edge Fetching Logic:**
  - Build TanStack Start `server functions` to query Neon through Hyperdrive.
  - Implement TanStack Query for client-side caching and state management.
- [ ] **UI Implementation:**
  - Basic Dashboard layout using Tailwind CSS.
  - League/Club switching logic using TanStack Router's search params.

**Deliverables:**

- Live dashboard fetching data from Neon.
- Seamless switching between leagues with zero-latency UI updates via TanStack Query.

---

## 5. Phase 4: Hardening & Monitoring

**Objective:** Ensure the system is production-ready and observable.

### Tasks:

- [ ] **Edge Testing:**
  - Implement **Vitest** for unit tests of utility functions.
  - Setup **Playwright** for E2E testing of the deployed preview URLs.
- [ ] **Monitoring & Performance:**
  - Configure **BetterStack** or **Axiom** for structured logging from the edge.
  - Final audit of Hyperdrive "Cache Hit" rates in the Cloudflare dashboard.

**Deliverables:**

- Final DevOps report (Latency improvements, Build times, Test coverage).
- Fully automated, monitored, and accelerated football statistics platform.

---

## 6. Tech Stack Summary

- **Framework:** TanStack Start (Nitro/Vinxi)
- **Deployment:** Cloudflare Pages (Edge Functions)
- **Database:** Neon (Serverless Postgres)
- **ORM:** Drizzle ORM
- **Acceleration:** Cloudflare Hyperdrive
- **CI/CD:** GitHub Actions + CodeRabbit
- **Testing:** Vitest + Playwright

---

### 📋 System Blueprints

_Standardized architectural templates for rapid, high-integrity deployment._

#### [Production API Blueprint (v1.0)](./blueprints/production-api-blueprint.md)

**Core Stack:** Bun | Express 5 | Drizzle | Neon | Arcjet

A technology-agnostic framework designed to bridge the gap between rapid prototyping and production-grade stability. This blueprint codifies my standards for:

- **Modular Monolith Architecture:** Explicit separation of Controllers, Services, and Models.
- **"Shift-Left" Security:** Integrated rate limiting, bot detection, and shield protection via Arcjet.
- **Type-Safe Contracts:** Runtime validation using Zod and end-to-end type safety with Drizzle ORM.
- **Agentic Compatibility:** Optimized for AI-assisted orchestration by defining strict code conventions and directory structures.

---

#### 3. [Project: Genesis] — **Conceptual Staging**

**Status:** Early Research / Security Audit  
**The Goal:** Building a production-grade SaaS product with a **"Shift-Left" Security** mindset.

#### Real Estate Systems (Project: Heritage-Refactor)

**Status:** Archived / Foundation Research  
**Outcome:** Validated the Hybrid Cloud Strategy (Edge + Regional).

This project was the crucible for understanding:

- **Compute:** Next.js/Prisma → TanStack Start/Drizzle (opening the hood)
- **Infrastructure:** Cloudflare Edge (speed) vs. AWS Regional (integrity)
- **Data:** Spatial queries (Mapbox) + ACID compliance requirements

**Key Learning:** The "Vending Machine vs. Warehouse" mental model works. Edge for distribution, Regional for truth.

**Current Status:** Insights extracted and applied to active projects (Transparency Dashboard, Football Dashboard). Not actively developed.

# Case Study: Canvas Cameo Architectural Refactor

**Status:** Archived / High-Integrity Stable State  
**Date:** January 14, 2026  
**Focus:** Microservices Decommissioning & Next.js 15 Modernization

---

## 🔍 The Architectural Post-Mortem

### The "Distributed Monolith" Trap

The original V1 prototype was built using a **Distributed Systems** approach (Microservices). While conceptually scalable, for a solo-engineer project, it resulted in a "Distributed Monolith."

**The Symptoms:**

- **Microservices Tax:** High operational overhead for negligible scaling benefits.
- **Contract Drift:** Frequent mismatches between the API Gateway and downstream services.
- **Configuration Fatigue:** Mismatched environment variables (`MONGO_URI` vs `MONGODB_URI`) leading to runtime failures.
- **Auth Complexity:** Difficulty maintaining consistent user context across multiple service boundaries.

---

## 🏗️ The Pragmatic Pivot: The Modular Monolith

To restore developer velocity and system integrity, the architecture was migrated to a **Type-Safe TypeScript Modular Monolith**.

### Key Backend Improvements:

- **Consolidation:** Merged the API Gateway, Design, Upload, and Subscription services into a single Express.js instance.
- **Type Safety:** Migrated from plain JavaScript to TypeScript with Zod-validated environment loading.
- **Auth Centralization:** Implemented a single, typed middleware for Google `id_token` verification, eliminating the need for gateway-level header injection.
- **Operational Simplicity:** Reduced the deployment target from 4 services to 1, simplifying logs, metrics, and local development.

---

## 🌐 Frontend Modernization (Next.js 15)

The frontend was refactored to align with modern **App Router** patterns and secure data-fetching strategies.

### Implementation of the BFF Proxy Pattern:

- **Server-Side Auth:** Introduced a Next.js BFF (Backend-for-Frontend) proxy route (`/api/backend/*`).
- **Token Injection:** The proxy route intercepts requests and injects the `Authorization` bearer token server-side using `auth()` (NextAuth v5).
- **Zero Client Leakage:** No session tokens or sensitive logic are exposed to the browser.
- **Prefetching:** Core pages (Home, Editor) now utilize Server Components to prefetch data, reducing client-side "layout shift" and `useEffect` dependency hell.

---

## 🛡️ Integrity Standards

The refactor concluded by re-instating strict quality gates that were previously bypassed:

- **Clean Builds:** Re-enabled strict TypeScript and ESLint build gates.
- **Type-Safe Contracts:** Established a 100% "Green Build" status, ensuring the frontend and backend remain in sync via shared types.
- **Dependency Management:** Resolved legacy version mismatches and pinned the stack to stable, modern releases.

---

## 📝 Final Lesson

Engineering integrity isn't about using the "coolest" architecture (Microservices); it's about choosing the architecture that fits the **product requirements** and **team velocity**.

**Canvas Cameo is now preserved as a stable, high-performance case study in architectural pragmatism.**

---

_“Architecture is the product.”_

---

### 🛡️ Security & Systems Intelligence

_Active exploration into the intersection of performance, resiliency, and adversarial security._

#### **Adversarial Security & LLM-Driven Threats**

- **Client-Side Injection (React2Shell):** Engineering strict sanitization and Content Security Policy (CSP) strategies to prevent client-side state from being utilized as a shell entry point.
- **Edge-Side Mitigation:** Implementing behavior-based bot detection using **Arcjet** and **Cloudflare WAF** to protect systems from automated AI-driven scrapers.

#### **Systems Architecture Research**

- **The Saga Pattern:** Investigating distributed transaction management to maintain consistency in event-driven systems.
- **Memory-Safety & Go:** Exploring the offloading of performance-critical middleware to **Go (Golang)** to leverage its superior concurrency model for security-critical request validation.

---

### 🏗️ Architectural Patterns & Infrastructure

_Current benchmarks and infrastructure decision-matrices._

#### **Storage & Database: The "Integrity vs. Reach" Matrix**

- **Object Storage (S3 vs. R2):**
  - **AWS S3:** Selected for legacy enterpise architecture and massive datasets requiring high-compliance internal storage.
  - **Cloudflare R2:** Selected for modern applications requiring frequent user-access with **$0 Egress (Exit Data) fees**, significantly reducing scaling costs for media-heavy platforms.
- **The Relational Layer:**
  - **AWS RDS (Postgres):** Designated for "Heavy State" requiring complex relationships and enterprise-grade ACID compliance.
  - **Cloudflare D1 (SQLite):** Designated for "Light State" at the edge, prioritizing speed and minimal cost for simpler data models.
- **Infrastructure Rule (Decoupling):** Separating Metadata (Database: ownership, sizes, URLs) from Media (Object Storage: raw bytes). This keeps the database lean and storage costs predictable.

#### **Compute: Edge vs. Regional Serverless**

- **Regional (AWS Lambda):** Best for heavy processing; execution stays in one data center. Subject to "Cold Starts."
- **Edge (Cloudflare Workers):** Global distribution with **Zero Cold Starts**. Utilizing "Isolates" instead of "Containers" for instant UI logic.
- **Cloudflare Hyperdrive:** Utilized as a Regional Database Accelerator. Combined with connection pooling and read-caching, it allows the "Heavy Truth" to stay in AWS RDS while achieving instant worldwide UX.
- **Statelessness:** Adopting a "Blank Slate" request model. Utilizing **AWS Cognito** for Identity and **AWS RDS** for Memory, allowing the Edge compute layer to remain ephemeral and high-performance.

---

### 🛠️ Current Research Domain

- **Frameworks:** TanStack Start, React 19, Go.
- **Data:** Drizzle ORM, PostgreSQL (Spatial Indexing/GiST), Redis.
- **Infrastructure:** AWS (IAM, S3, RDS), Cloudflare (Workers, R2, D1, Hyperdrive).
- **Observability:** Sentry, BetterStack (Uptime & Logging).

---

### 📝 The Engineering Stance

I believe that frameworks are tools, but **Architecture is the product**. We are currently in an era of "convenience-first" deployment where high-level abstractions (like Vercel) allow for rapid prototyping. While valuable for initial velocity, I believe that true system integrity requires a deep understanding of the entire production process.

My architectural decisions are driven by the specific needs of the product:

- **Product Requirements:** Aligning infrastructure with the core user experience.
- **Economic Scaling:** Choosing between the global speed of Edge Isolates and the high-trust integrity of Regional Compute based on user demographics and team size.
- **Developer Responsibility:** Moving beyond "magic" abstractions to take full ownership of the data layer (Drizzle/SQL) and the network lifecycle.

---

_“Integrity starts in the research phase.”_
