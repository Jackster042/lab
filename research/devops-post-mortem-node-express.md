# Comparative Study: Node/Express vs. Edge-Native

**Status:** Completed Study | **Last Updated:** Jan 02, 2026

## 🎯 Objective

Extracting successful patterns from legacy DevOps projects (Node/Express) and translating them to the Cloudflare/Neon ecosystem.

## ✅ Patterns to Port

- **Testing:** Adapting Vitest patterns from Node to work within the `miniflare` or `workerd` environment.
- **Monitoring:** Translating standard Express middleware logging into structured Cloudflare Worker logs.
- **Containerization:** Using the previous Docker setup as a baseline for local development parity, even when the final target is serverless.

## ⚠️ Infrastructure Gaps

- **Middleware Complexity:** Node.js has a massive ecosystem of "batteries-included" middleware that often relies on Node-specific APIs (FS, Crypto) not natively available in Edge Isolates.
