# 001 — System Architecture (Desktop Session)

**Date:** 2026-02-08
**Source:** `payment-platform-architecture.docx`

## Summary

Comprehensive architecture for an enterprise-grade payment processing platform for core banking. Kafka-driven, event-sourced, ISO 20022 native. Multi-region: Singapore, Hong Kong, UK, India.

## Key Concepts

### 6-Tier Architecture
1. **Ingestion Gateway** — Protocol translation, dedup (Redis TTL 7d), envelope wrapping
2. **Message Processing** — Schema validation, MT→MX conversion, enrichment (BIC, IBAN, FX, fees)
3. **Compliance & Screening** — Sanctions (OFAC/EU/UN/MAS), AML, Fraud ML, PEP. Fan-out/fan-in pattern
4. **Routing & Clearing** — Adapters per clearing house (MEPS+, FAST, CHATS, FPS, SWIFT gpi). Circuit breaker protected
5. **Accounting & Settlement** — Double-entry ledger, 5-step Saga with compensating transactions
6. **Reporting & Reconciliation** — Kafka Streams → ClickHouse → GraphQL dashboards

### Payment State Machine
RECEIVED → VALIDATED → ENRICHED → SCREENING → SCREENED_PASS → SUBMITTED → CONFIRMED → BOOKED → COMPLETED
Failure states: REJECTED, CLEARING_TIMEOUT, RETURNED

### Kafka Topics (10 operational + DLQ)
- payments.inbound.raw (24 partitions, RF=3, 30d)
- payments.parsed.canonical
- payments.enriched
- payments.compliance.request/response
- payments.clearing.outbound/response
- payments.accounting.booked
- payments.status.changes (compacted)
- payments.dlq.*

### Database-per-Service
- ingestion_db (PG16, 50GB/mo)
- payment_master_db (PG16 + Citus, 200GB/mo)
- reference_data_db (PG16 + Redis, 10GB)
- compliance_db (PG16, 100GB/mo)
- routing_db (PG16, 80GB/mo)
- ledger_db (PG16 + Citus, 500GB/mo)
- analytics_db (ClickHouse, 1TB/mo)
- event_store (Kafka log)

### Implementation Roadmap
- Phase 1 (8w): Foundation — Kafka, Ingestion, Message Processing
- Phase 2 (6w): Compliance — Screening, AML, Investigation
- Phase 3 (8w): Clearing — Adapters, Accounting, Saga
- Phase 4 (4w): Operations — Reporting, Monitoring, Hardening

## Original Files
- `docs/Design/payment-architecture.html` (interactive visual)
- `docs/Design/payment-flow-diagram.html` (interactive flow diagram)
- `temp_extract/payment-platform-architecture.docx` (source document)
