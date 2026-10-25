# Phase 10 — Performance and Targeted Backend Optimization

**Status:** Planned / not yet analyzed.

## Goals
Identify real bottlenecks before proposing caching, Redis, additional workers, indexes or other infrastructure.

## Investigation order
1. Establish reproducible workload and baseline: throughput, p50/p95/p99 latency, error rate, memory and DB utilization.
2. Instrument/request-trace the slow paths.
3. Separate application computation, SQL, serialization, network and provider latency.
4. Inspect SQL plans and returned row counts.
5. Check redundant reads, N+1 patterns, large payloads and sequential calls that could safely run in parallel.
6. Optimize the smallest proven bottleneck.
7. Compare results and note any new consistency/operational cost.

## Redis assessment
Potential use cases:
- Cache expensive repeated reads when staleness/invalidation is manageable.
- Shared rate limiting across multiple backend instances.
- Coordination/short-lived state where a local process cannot provide the required semantics.
- Queue backend if a durable asynchronous-work requirement has been established.

Do not cache secrets or user-specific values under keys that could mix users. Define TTL, invalidation, cache-miss behavior and failure handling.

## Queue assessment
Consider a worker queue for slow or retryable email, reminders, exports or provider sync when HTTP latency/reliability requirements justify decoupling. Ensure jobs have idempotency strategy, retry/backoff policy, failure visibility and bounded concurrency.

## Deliverables
- Bottleneck ranking linked to source and measurement.
- Before/after measurements.
- Architecture decision notes for each proposed technology.
- A “do not add” list for optimizations that do not solve a demonstrated problem.

## Exit criteria
- Every recommended optimization has a problem statement, evidence, trade-offs and measurement plan.
