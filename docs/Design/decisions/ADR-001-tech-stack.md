# ADR-001: Technology Stack Selection
**Status:** Accepted
**Date:** 2026-02-08

## Context
Building an enterprise payment processing platform that handles multi-region clearing houses (SG, HK, UK, IN) with sub-second SLAs, regulatory compliance, and 99.99% availability. Need event-driven architecture with replay capability for audits.

## Decision
- **Java 21** with Spring Boot 3.3+ (virtual threads for concurrency)
- **Apache Kafka 3.7+** as event backbone (not RabbitMQ or Pulsar)
- **PostgreSQL 16 + Citus** for OLTP with horizontal sharding
- **ClickHouse** for analytics (columnar, 100x faster aggregation)
- **Redis Cluster 7.2+** for caching, dedup, idempotency
- **Kubernetes (EKS/GKE)** with Istio service mesh
- **HashiCorp Vault** for dynamic secrets

## Alternatives Considered
- **RabbitMQ** — Better for task distribution but lacks event replay, ordering guarantees, and exactly-once semantics needed for payment audit trails
- **Pulsar** — Capable but less mature ecosystem, fewer production references in banking
- **MongoDB** — Rejected for OLTP due to weaker ACID guarantees for financial ledger
- **TimescaleDB** — Considered for analytics but ClickHouse benchmarks faster for our aggregation patterns

## Consequences
- Java ecosystem provides mature libraries for ISO 20022 (JAXB), SWIFT, financial protocols
- Kafka replay enables disaster recovery and regulatory audit without separate audit infrastructure
- Citus sharding adds operational complexity but necessary for ledger scale (500GB/mo)
- Team needs Kafka expertise — significant learning investment
