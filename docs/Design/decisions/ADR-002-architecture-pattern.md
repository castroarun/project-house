# ADR-002: Hexagonal Architecture + Event Sourcing
**Status:** Accepted
**Date:** 2026-02-08

## Context
Need an architecture that: (1) isolates business logic from infrastructure (clearing houses, Kafka, databases), (2) supports adding new clearing houses without modifying existing code, (3) provides complete audit trail for regulatory compliance, (4) enables disaster recovery via event replay.

## Decision
- **Hexagonal Architecture (Ports & Adapters)** — Domain at center with zero framework imports
- **Event Sourcing** — Kafka log as source of truth, databases as materialized views
- **Database-per-Service** — Each microservice owns its database exclusively
- **Saga Pattern** — For distributed accounting transactions with compensating actions

## Alternatives Considered
- **Layered Architecture** — Simpler but creates tight coupling between layers; clearing house changes ripple through
- **CQRS without Event Sourcing** — Loses replay capability and audit trail completeness
- **Shared Database** — Simpler operations but prevents independent scaling and schema evolution

## Consequences
- Domain layer is testable without any infrastructure (Spring, Kafka, Redis)
- Adding a new clearing house = new adapter class, zero existing code changes (OCP)
- Event replay enables full state reconstruction — databases become disposable
- Higher complexity: developers must understand hexagonal boundaries and event sourcing patterns
- Saga compensations must be carefully designed — each step idempotent
