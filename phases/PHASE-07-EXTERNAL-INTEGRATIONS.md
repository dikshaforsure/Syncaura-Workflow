# Phase 7 — External Integrations and Provider APIs

**Status:** Planned / not yet analyzed.

## Goals
Map the integration boundary for Google OAuth/Calendar, Microsoft Graph/Outlook, email delivery, Slack, GitHub and AI providers where source call sites establish that they are actually used.

## Files to inspect
- `src/services/googleCalendar.js`
- `src/services/emailService.js`, `src/utils/email.js`
- `src/services/slackBot.js`
- `src/services/githubAPI.js`, `src/controllers/githubController.js`
- OAuth routes/controllers/utilities and token persistence queries
- `outlook-sync/` and its package/runtime configuration
- Chatbot/controller service and AI-related source integration references

## Deliverables
- Provider authorization and API request sequence diagrams.
- Scopes, secrets, token lifetime, refresh/revocation, and storage map.
- Timeout, error normalization, quota/rate-limit, and retry behavior.
- Data minimization and safe logging review.
- List of integrations proven active versus standalone/legacy/uncertain.
- Interview case study for the reported Google Calendar consent design.

## Questions to answer
- Is a provider call made inside an HTTP request or background task?
- What happens if the provider is unavailable?
- Are side effects safe to retry?
- Are tokens bound to the correct Syncaura user?
- Are callback URLs and OAuth state validated?
- Are response fields and tokens ever logged or sent to the browser unnecessarily?

## Exit criteria
- All integration call sites are mapped.
- The Calendar-consent story is separated from code details not yet verified.
- No provider integration is called production-ready without concrete evidence.
