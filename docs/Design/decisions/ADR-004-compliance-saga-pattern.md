# ADR-004: Compliance Screening — Internal Async Saga (Option A)
**Status:** Accepted
**Date:** 2026-02-21

## Context
Tier 3 Compliance runs 4 screening engines in parallel: Sanctions (OFAC/EU/UN/MAS), AML (Transaction Monitoring), Fraud (ML Scoring), and PEP Screen. We need a pattern for fan-out (dispatch all 4) and fan-in (aggregate results before proceeding to Tier 5 Accounting).

Two options were considered:
- **Option A:** Internal async — all 4 engines run as parallel tasks (threads/coroutines) inside a single Tier 3 microservice
- **Option B:** Kafka sub-topics — each engine is a separate microservice with its own Kafka request/response topics

## Decision
**Option A — Internal async within a single Tier 3 Compliance service.**

The Compliance Orchestrator service:
1. Consumes from `payments.enriched`
2. Fires 4 async tasks simultaneously (one per engine)
3. Each engine is a separate module/library within the service
4. An aggregator waits for all 4 futures to resolve
5. Maintains a correlation record per `paymentId`:
   ```json
   {
     "paymentId": "PAY-2026-0001",
     "sanctions": null,
     "aml": null,
     "fraud": null,
     "pep": null,
     "timeout": 3000
   }
   ```
6. As each result completes, the slot is filled
7. When all 4 are filled:
   - **All PASS** → publish single event to `payments.compliance.passed`
   - **Any FAIL** → publish to `payments.compliance.failed` (triggers ACSC RJCT)
   - **Timeout** → treat as FAIL with reason `COMPLIANCE_TIMEOUT`

Tier 5 only ever sees ONE event — it does not know or care about the 4 internal engines.

## Alternatives Considered
**Option B — Kafka sub-topics per engine:** Each compliance engine as its own microservice, communicating via Kafka topics (`compliance.sanctions.check` → `compliance.sanctions.result`, etc.). The orchestrator would consume all 4 result topics.

Rejected for Phase 1 because:
- Adds 8 extra Kafka topics (4 request + 4 response)
- Increases deployment complexity (5 services instead of 1)
- Higher latency from Kafka round-trips between engines
- Harder to debug — distributed tracing across 5 services for one logical operation
- The 4 engines don't need independent scaling at MVP volume

## Consequences
- **Simpler deployment:** Single service, single container for all compliance logic
- **Lower latency:** ~50-200ms total (in-process calls vs Kafka round-trips)
- **Easier debugging:** All 4 checks visible in one service's logs
- **Trade-off:** All 4 engines must be deployed together — updating Sanctions requires redeploying the whole compliance service
- **Migration path:** Option B remains viable for Phase 2/3 when engines need independent scaling, versioning, or third-party vendor integration. The internal module boundaries are designed to make this extraction straightforward.
