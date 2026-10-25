# Phase 6 — Business Logic and Feature Workflows

**Status:** Planned / not yet analyzed.

## Goals
Explain how each significant product feature operates across frontend, API, authorization, data persistence, notifications and real-time events. Select feature groups from the repository rather than assuming every README-listed feature is complete.

## Initial feature groups to trace
- Projects and project membership
- Tasks, dependencies, subtasks and reminders
- Channels and messages
- Documents and attachments
- Meetings
- Attendance and leave
- Complaints, notices, notes and notifications
- Dashboards and reports
- Accounts, profiles, admin and co-admin workflows

## Per-feature workflow
1. User intent and feature problem.
2. Frontend component/API caller.
3. Request method and mounted route.
4. Middleware, identity and role/ownership conditions.
5. Controller validation and business rules.
6. Database reads/writes and transaction boundaries.
7. Notifications, Socket.IO events, email or provider calls.
8. Response shape and frontend state update.
9. Failure modes and tests.
10. Optimization risks supported by the inspected code.

## Deliverables
- One workflow diagram per major feature group.
- Feature-to-route/controller/table matrix.
- Cross-feature dependencies and duplicated logic.
- Prioritized correctness or maintainability findings.
- Interview-ready explanations of the features personally understood/owned.

## Exit criteria
- Every major feature group is mapped at least once.
- Each claim points to implementation evidence.
- Partially implemented or disconnected features are identified clearly.
