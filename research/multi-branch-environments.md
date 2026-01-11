# Research: Multi-Branch Cloud Environments

**Status:** Active | **Last Updated:** Jan 02, 2026

## 🎯 Objective

Establishing a mirrored development lifecycle where Database (Neon), Edge Compute (Cloudflare), and Meta-framework (TanStack Start) are synchronized across `dev`, `preview`, and `main` branches.

## 🛠 Current Configuration

- **Production:** `main` branch -> Cloudflare Pages (Production) -> Neon `main` (via Hyperdrive).
- **Staging:** `preview` branch -> Cloudflare Pages (Preview) -> Neon `preview-branch`.
- **Development:** Localhost -> Wrangler Proxy -> Neon `dev-branch`.

## 🚧 Encountered Friction

- **Hyperdrive Constraints:** Hyperdrive is a production-level accelerator; simulating its behavior in local development without latency spikes is a primary challenge.
- **Connection String Management:** Drizzle must dynamically switch between the Hyperdrive pooled URL (Prod) and the direct Neon WebSocket/HTTP connection (Dev).
- **Environment Parity:** TanStack Start (Vinxi/Nitro) requires specific configurations to ensure the local development server respects the Cloudflare Worker environment variables.

## 💡 Key Learnings

- **Manual Gatekeeping:** High-trust tasks (branch creation, secret rotation) must remain human-driven.
- **Wrangler Proxying:** Essential for local testing of edge-specific bindings.

## 🔍 The "Quiet Period" Audit (Jan 11, 2026)
- **Observation:** System remained idle for 72+ hours during holiday break.
- **Integrity Check:** Production deployments on Cloudflare Pages remained stable; no "zombie" processes or configuration drifts in the Neon/Hyperdrive tunnel.
- **Conclusion:** The automated "Plumbing" established in Phase 1 is officially validated for stability. The focus now shifts from "Will it hold?" to "How do we scale the workflow?"
