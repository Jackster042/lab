# Lab / Experiments

Personal sandbox for learning distributed systems, architecture patterns, and new technologies. 
**Rule:** If it's here, it's unfinished, broken, or conceptual.

---

## Current Experiments

### ⚽ Sports Data Sync (Backend)
**Status:** Early prototype (Node.js + WebSocket)

Exploring real-time broadcast patterns for live sports scores.
- Basic Express + `ws` server working (single-node)
- Learning: Redis Pub/Sub for horizontal scaling (not implemented yet)
- Learning: Binary protocols (MessagePack) for efficiency

**What's working:** Local WebSocket broadcast  
**What's not:** Multi-instance scaling (needs Redis)

---

### 🧠 On-Device ML (Research)
**Status:** Reading/Design only

Exploring TensorFlow.js for privacy-preserving recommendations.
- Literature review on federated learning concepts
- No code yet; architecture sketches only

---

## Archived Projects

### Canvas Cameo Refactor (2024)
**Status:** Completed learning project

Refactored a microservices prototype into a modular monolith.
**Lesson learned:** Microservices tax isn't worth it for solo projects.
**Code:** [Link to actual repo if you have it, otherwise notes only]

---

## Blueprints & Notes

### Production API Template
A personal boilerplate for Node.js APIs (Bun + Express + Drizzle + Arcjet).
- **Purpose:** Starting point for future projects
- **Status:** Template only, not a running system

### Case Studies
Post-mortems and architecture decisions from past projects (see `/case-studies`).

---

## Research Log

**Currently reading about:**
- Saga pattern for distributed transactions
- Edge vs Regional compute trade-offs
- Connection pooling (Hyperdrive, PgBouncer)

**Note:** These are learning notes, not production systems.

---

**Philosophy:** This is my digital garden - messy, experimental, and honest about what's broken.
