---
Status: Architecture Concept
Last Updated: [Date]
Code Status: Not implemented (React Native learning planned)
---

# Mobile Edge Computing Concepts

Exploring React Native + Edge functions. No prototype built yet.

## 🎯 Objective

Exploring the feasibility of a mobile-first client interacting with a global Edge backend.

## 🏗 High-Level Architecture

- **Client:** React Native (Expo) vs. PWA.
- **Backend:** Cloudflare Workers (Edge Functions).
- **Data Persistence:** Neon (PostgreSQL).
- **State Management:** TanStack Query for offline-first capabilities.

## ❓ Open Questions

1. **The Latency Tax:** Does the "Edge" advantage still hold for mobile networks with higher base latency?
2. **Auth Integration:** Leveraging AWS Cognito or Clerk in a cross-platform (iOS/Android/Web) environment with Edge Runtimes.
3. **Synchronization:** Effective strategies for bi-directional sync between local SQLite (mobile) and Postgres (Edge).

## 📅 Next Steps

- Researching Expo's compatibility with TanStack Query's persistent caching.
- Benchmarking request times from 5G/LTE networks to Cloudflare PoPs.
