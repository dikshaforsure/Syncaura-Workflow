# Phase 3 — API Routes, Middleware, and Request Handling

**Status:** Planned / not yet analyzed.

## Goals
- Enumerate mounted endpoint paths, HTTP methods, handlers, validation and required identity/role checks.
- Trace the full path from Axios call to route, middleware, controller, database/external side effect, and response.
- Identify inconsistent response shapes, status codes, missing validation, and route shadowing only when supported by source evidence.

## Files to inspect
- `Syncaura-backend/src/app.js`
- All files under `Syncaura-backend/src/routes/`
- `Syncaura-backend/src/middlewares/`
- `Syncaura-backend/src/validators/`
- Corresponding frontend API calls under `Syncaura-frontend/src/`

## Deliverables
1. Endpoint catalogue: method, path, handler, auth, roles, validation, request/response schema.
2. Route-to-controller dependency map.
3. Mermaid request lifecycle diagrams for representative critical workflows.
4. Finding table with evidence, impact, confidence, and recommendation.
5. Interview Q&A on REST semantics, status codes, middleware ordering, input validation, and error propagation.

## Trace template
For each endpoint, record:
- Frontend call site and API base URL.
- Mounted route path and HTTP method.
- Middleware chain and order.
- Expected request parameters/body.
- Controller and persistence/external calls.
- Success response/status.
- Expected failure modes and status codes.
- Authentication/authorization and resource-ownership checks.
- Tests or reproducible validation.

## Exit criteria
- Every mounted route file is catalogued.
- Critical paths have been traced end to end.
- Uncertain behavior is explicitly marked for runtime verification.
- Recommendations are based on concrete endpoint evidence.
