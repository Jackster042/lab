# Research: Convex as a B2B Infrastructure Provider
**Status:** Exploring | **Last Updated:** Jan 11, 2026

## 🎯 Objective
Evaluating Convex as an alternative to the Neon/Hyperdrive/Drizzle stack for high-velocity B2B application development.

## ⚖️ Comparison: The "Integrity" Trade-off
- **Neon Stack:** High control, standard SQL, portable, manual plumbing (Hyperdrive/Auth/Caching).
- **Convex:** Low plumbing, built-in reactivity, proprietary runtime, integrated caching.

## 🛠 Features to Validate
- **ACID Transactions:** How Convex handles multi-document updates compared to PostgreSQL.
- **Edge Performance:** Benchmarking Convex's "Action" latency vs. Cloudflare Workers.
- **B2B Scaling:** Evaluating multi-tenancy patterns and row-level security (RLS) within the Convex environment.

## 🚧 Potential Friction
- Moving away from standard SQL (PostgreSQL) might conflict with the "Fundamentals First" thesis.
- Proprietary lock-in vs. the "Vending Machine/Warehouse" hybrid strategy.
