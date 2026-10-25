# Phase 5 — PostgreSQL Schema, Queries, and Data Integrity

**Status:** Planned / not yet analyzed.

## Goals
Understand entities, relationships, constraints, query patterns, connection management, transactions, migration behavior and how the database enforces business invariants.

## Files to inspect
- `src/config/init.sql`
- `src/config/db.js` and `run-init.js`
- Every controller query using `pool.query`
- Model/helper files and migration-related scripts
- All schema changes in source and documentation

## Deliverables
- Entity relationship diagram based on actual DDL.
- Table inventory including primary keys, foreign keys, nullable columns, unique/check constraints and indexes.
- Query-to-endpoint map for critical workflows.
- Transaction/atomicity analysis.
- Migration reproducibility and startup/readiness review.
- Query/index improvements supported by query plans and representative workload.

## Query assessment
For each expensive or important query, capture its purpose, predicates, joins, sort/pagination, expected cardinality, relevant constraints/indexes, and failure behavior. Use `EXPLAIN (ANALYZE, BUFFERS)` only on a safe test dataset or controlled environment; do not run destructive experiments against production.

## Exit criteria
- Core tables and relationships are understood.
- Critical writes have explicit consistency semantics.
- Index recommendations reference real query shapes.
- Migration and connection-pool findings are distinguished from assumptions.
