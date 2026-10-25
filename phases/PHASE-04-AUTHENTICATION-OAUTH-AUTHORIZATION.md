# Phase 4 — Authentication, OAuth, Sessions, and Authorization

**Status:** Planned / not yet analyzed.

## Goals
Trace application identity separately from permissions to access Syncaura resources and third-party APIs. Focus on password authentication, JWT/session lifecycle, refresh behavior, Google OAuth, GitHub OAuth if active, role-based access, and resource ownership.

## Files to inspect
- `src/controllers/authController.js`, `src/controllers/oauthController.js`
- `src/routes/authRoutes.js`, `src/routes/googleAuth.route.js`, `src/routes/googleAuthRoutes.js`, `src/routes/github.routes.js`
- `src/middlewares/auth.js`, `userAuth.js`, `role.js`, `coAdminAuth.js`
- `src/utils/generateTokens.js`, `googleAuth.js`, `generateGoogleToken.js`
- User schema and frontend sign-in/callback/refresh flows
- Relevant environment templates and all token persistence call sites

## Deliverables
- Login, logout, token refresh, password reset and provider OAuth sequence diagrams.
- Scope and consent matrix for Google Calendar versus login.
- Where credentials and tokens travel and where they are stored.
- Role/resource authorization matrix.
- Review of OAuth state, redirect URI checks, least privilege, token expiry/revocation and safe logging.
- Tests for denial, expiration, invalid state, missing scopes and resource ownership.

## Important distinction
Authentication identifies the user. Application authorization determines what a user may do within Syncaura. Third-party delegated authorization allows specific access to external resources, such as Google Calendar. Do not conflate these flows.

## Exit criteria
- Every critical auth flow is traced to code.
- Token/session behavior is explicit.
- Positive and negative authorization scenarios are documented.
- Interview explanations distinguish implemented behavior from recommended hardening.
