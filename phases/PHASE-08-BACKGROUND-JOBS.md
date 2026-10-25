# Phase 8 — Schedulers, Background Work, and Reliability

**Status:** Planned / not yet analyzed.

## Goals
Trace reminder and scheduled-task execution, identify work that runs during import or process startup, and assess failure recovery, duplicate execution, concurrency and observability.

## Files to inspect
- `src/scheduler/reminderScheduler.js`
- `src/scheduler/emailReminder.js`
- `src/scheduler/meetingReminder.js`
- `src/scheduler/taskReminder.js`
- All notification/email services called from schedulers
- Server initialization, hosting/replica assumptions, database writes and job side effects

## Deliverables
- Scheduler registration and execution diagrams.
- Schedule/timezone and due-item selection rules.
- Failure/retry and duplicate-effect analysis.
- Concurrency behavior when multiple server instances run.
- Recommendation on existing scheduler versus a durable worker queue.
- Tests for retry, idempotency, overlapping execution and process restart.

## Queue decision rule
A queue is worth introducing when the workflow requires durable execution, backpressure, delayed retries, worker isolation or independent scaling. Redis/BullMQ is one possible implementation, not an automatic choice. A queue does not by itself guarantee exactly-once email or provider side effects.

## Exit criteria
- Scheduled workflows and side effects are traced.
- Duplicate and retry behavior is explained.
- Any queue recommendation is tied to a real operational requirement.
