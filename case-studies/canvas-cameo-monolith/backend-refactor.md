# Backend TypeScript Monolith Overview (vs legacy `server/` microservices)

## Why this doc exists

You asked to move the backend from **plain JavaScript microservices** to a **TypeScript modular monolith** for improved type safety and maintainability. This document summarizes what we implemented in `/backend` and compares it to the previous state under `/server`.

---

## Quick repo context (current state)

- **Legacy backend (microservices)**: `server/`
  - `api-getaway/` (gateway proxy + Google token verification)
  - `design-service/` (design CRUD/search)
  - `upload-service/` (uploads + Cloudinary + Stability AI)
  - `subscription-service/` (premium + PayPal)
- **New backend (monolith, TypeScript)**: `backend/`
  - Single deployable Express app that serves `/v1/*` directly (no gateway required)
- **Frontend**: `canvas_cameo/` (Next.js) calls `/v1/*`

---

## What we implemented in `backend/`

### 1) New TypeScript backend project (compiled runtime)

**Location**: [`backend/`](../backend/)

- **Build strategy**: compile TypeScript → `dist/` via `tsc`, run via `node dist/server.js`
- **Scripts**: [`backend/package.json`](../backend/package.json)
  - `npm run dev` uses `tsx watch` for local dev
  - `npm run build` runs `tsc`
  - `npm start` runs `node dist/server.js`

### 2) Typed environment loading + validation

**File**: [`backend/src/config/env.ts`](../backend/src/config/env.ts)

- Centralized env parsing using **Zod**
- Canonicalizes Google client ID via:
  - `GOOGLE_CLIENT_ID` or fallback `AUTH_GOOGLE_ID`

### 3) MongoDB connection for the monolith

**File**: [`backend/src/db/mongo.ts`](../backend/src/db/mongo.ts)

- Single Mongo connection for all modules

### 4) Typed auth middleware (Google `id_token`)

**File**: [`backend/src/middleware/auth.ts`](../backend/src/middleware/auth.ts)

- Verifies `Authorization: Bearer <id_token>` with `google-auth-library`
- Populates a typed user context on `req.user`:
  - Declared in [`backend/src/types/express.d.ts`](../backend/src/types/express.d.ts)

This eliminates the legacy pattern of “gateway verifies token → downstream services trust `x-user-id`” and prevents a whole class of runtime user-shape bugs.

### 5) Consistent response helpers

**File**: [`backend/src/http/respond.ts`](../backend/src/http/respond.ts)

We keep a consistent envelope the frontend already expects:

- `success: true|false`
- `message?: string`
- `data: ...`

### 6) `/v1` routing (no proxy rewrite)

**Files**:

- [`backend/src/app.ts`](../backend/src/app.ts)
- [`backend/src/routes/v1.ts`](../backend/src/routes/v1.ts)

The monolith mounts:

- `GET /health`
- `GET/POST/PUT/DELETE /v1/designs...`
- `GET/POST /v1/media...`
- `GET/POST /v1/subscription...`

### 7) Modules implemented with endpoint parity

#### Designs

**Files**:

- Model: [`backend/src/modules/design/model.ts`](../backend/src/modules/design/model.ts)
- Routes: [`backend/src/modules/design/routes.ts`](../backend/src/modules/design/routes.ts)

Endpoints:

- `GET /v1/designs`
- `GET /v1/designs/:id`
- `GET /v1/designs/search?q=...`
- `POST /v1/designs` (create + update via `designId` in body)
- `PUT /v1/designs` (explicit support for frontend behavior)
- `DELETE /v1/designs/:id`

#### Media (uploads + AI image generation)

**Files**:

- Model: [`backend/src/modules/media/model.ts`](../backend/src/modules/media/model.ts)
- Routes: [`backend/src/modules/media/routes.ts`](../backend/src/modules/media/routes.ts)
- Cloudinary: [`backend/src/integrations/cloudinary/`](../backend/src/integrations/cloudinary/)
- Stability AI: [`backend/src/integrations/stability/textToImage.ts`](../backend/src/integrations/stability/textToImage.ts)

Endpoints:

- `GET /v1/media/get`
- `POST /v1/media/upload` (multipart via multer)
- `POST /v1/media/ai-image-generate`

#### Subscription (PayPal)

**Files**:

- Model: [`backend/src/modules/subscription/model.ts`](../backend/src/modules/subscription/model.ts)
- Routes: [`backend/src/modules/subscription/routes.ts`](../backend/src/modules/subscription/routes.ts)
- PayPal: [`backend/src/integrations/paypal/client.ts`](../backend/src/integrations/paypal/client.ts)

Endpoints:

- `GET /v1/subscription`
- `POST /v1/subscription/create-order`
- `POST /v1/subscription/capture-order`

Notable improvement vs legacy: **`capture-order` derives user identity from auth**, not from `userId` in the request body.

---

## Render + Vercel cutover artifacts

### Render helper

**File**: [`render.monolith.yaml`](../render.monolith.yaml)

Defines a single Render web service using:

- Build: `cd backend && npm ci && npm run build`
- Start: `cd backend && npm start`

### Vercel frontend setting

Set `NEXT_PUBLIC_API_URL` to the Render monolith base URL so `canvas_cameo/services/*` calls hit the monolith.

---

## Comparison: `backend/` monolith vs `server/` microservices

### Topology

- **Before (`server/`)**:
  - Multiple services + gateway proxy with `/v1` → `/api` rewrite
  - Auth verified in gateway then forwarded as `x-user-id` headers
- **After (`backend/`)**:
  - Single service handles `/v1/*` directly
  - Auth verified once per request in-process, typed `req.user`

### Contract stability

- **Before**: contract drift existed between frontend and services:
  - Frontend using `PUT` where backend only registered `POST`
  - Subscription capture mismatch (`{ orderId }` vs `{ orderId, userId }`)
- **After**: monolith supports both:
  - `POST /v1/designs` and `PUT /v1/designs`
  - Capture uses authenticated user, so frontend doesn’t need to send `userId`

### Configuration drift

- **Before**: mismatched env names caused runtime failures:
  - `MONGO_URI` vs `MONGODB_URI`
  - Cloudinary casing differences
- **After**: monolith uses a single env contract enforced via Zod (`env.ts`)

### Type safety + correctness

- **Before**: plain JS + inconsistent `req.user` shapes across services (easy to break at runtime)
- **After**:
  - Request user context is typed via module augmentation
  - Input validation is explicit (Zod schemas per endpoint)
  - TS compilation acts as a safety net for refactors

### Operational complexity

- **Before**: multiple Render services, internal URLs, gateway routing, and cross-service debugging
- **After**: one backend deployable unit (fewer moving parts, simpler logs/metrics, easier local dev)

---

## Known gaps / follow-ups (recommended next)

- **Frontend config cleanup**:
  - Ensure all frontend API calls use `NEXT_PUBLIC_API_URL` consistently (currently some code uses `API_URL`)
  - Fix any request-body double-serialization in the frontend client (if still present)
- **CORS policy**:
  - Monolith currently uses permissive `cors({ origin: true })`; decide on an allowlist like the gateway used
- **Error handling**:
  - Convert more route-level failures to consistent typed errors (and avoid leaking internal messages in prod)
- **Tests**:
  - Add smoke tests for `/health` and the `/v1/*` endpoints (especially uploads + PayPal stubs)
- **Decommission plan**:
  - Once frontend points to the monolith and flows are verified, retire `server/api-getaway` + other services
