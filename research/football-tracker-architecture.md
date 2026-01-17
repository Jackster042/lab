### ⚽ Football Match Tracker (Extension → Mobile)

**Status:** Architecture Phase / Design Validated  
**The Goal:** A cross-platform live score tracker utilizing a "Canonical Backend" strategy on Cloudflare Edge.

- **Infrastructure:** Cloudflare Workers + KV (Polling & Caching).
- **Core Strategy:** API calls scale with leagues/matches, not with users.
- **Internal Domain:** Custom mapping for `MatchStatus` and `MatchEvent` to ensure provider-agnostic logic.
- **[Read the Full Design Doc](./research/football_tracker_architecture.md)**
