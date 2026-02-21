# Payment House — Design Brief

**Product Name:** Payonex
**Status:** Evolving (Conception Stage)
**Last Updated:** 2026-02-21
**Source Sessions:** 001-system-architecture, 002-coding-standards-design-patterns

---

## Vision

**Payonex** — Enterprise-grade payment processing platform for core banking. Handles the complete lifecycle of domestic and cross-border payments across Singapore, Hong Kong, UK, and India.

## Core Architecture

**Kafka-driven, event-sourced microservices** organized into 6 architectural tiers:

1. Ingestion Gateway — Multi-protocol entry (IBM MQ, SFTP, REST/gRPC, ISO 20022)
2. Message Processing — Validation, MT→MX conversion, enrichment
3. Compliance Screening — Sanctions, AML, Fraud, PEP (parallel fan-out/fan-in)
4. Routing & Clearing — Country-specific adapters (MEPS+, FAST, CHATS, FPS, SWIFT gpi)
5. Accounting & Settlement — Double-entry ledger, Saga orchestration
6. Reporting & Reconciliation — Real-time dashboards, regulatory reports, EOD recon

## Tech Stack (Decided)

| Layer | Technology |
|---|---|
| Language | Java 21 (Virtual Threads) |
| Framework | Spring Boot 3.3+ |
| Event Streaming | Apache Kafka 3.7+ |
| Primary DB | PostgreSQL 16 + Citus |
| Cache | Redis Cluster 7.2+ |
| Analytics | ClickHouse |
| CDC/Outbox | Debezium 2.5+ |
| Orchestration | Kubernetes (EKS/GKE) |
| Service Mesh | Istio 1.21+ |
| Secrets | HashiCorp Vault |
| Config | Consul / etcd |
| Observability | Prometheus + OpenTelemetry + Grafana |
| CI/CD | GitLab CI + ArgoCD |

## Key Design Patterns

- Hexagonal Architecture (Ports & Adapters)
- Domain-Driven Design (6 Bounded Contexts)
- Event Sourcing (Kafka as source of truth)
- Saga Pattern (5-step accounting with compensating txns)
- Strategy Pattern (pluggable clearing adapters)
- Anti-Corruption Layer (per clearing house)
- Circuit Breaker (Resilience4j)
- Transactional Outbox (Debezium CDC)

## Multi-Region

| Region | Primary Clearing | Retail Real-Time |
|---|---|---|
| Singapore | MEPS+ (MAS) | FAST (ABS) |
| Hong Kong | HKD CHATS (HKICL) | FPS (HKICL) |
| United Kingdom | CHAPS (BoE) | Faster Payments (VocaLink) |
| India | RTGS (RBI) | UPI/IMPS (NPCI) |

## SLA Targets

- FAST E2E: <5s (p99)
- RTGS E2E: <15s (p99)
- Ingestion: 10K msg/s
- Availability: 99.99%
- MTTD: <30s
- MTTR: <2min (auto)

## Implementation Phases

| Phase | Duration | Scope |
|---|---|---|
| Phase 1: Foundation | 8 weeks | Kafka + Ingestion + Message Processing |
| Phase 2: Compliance | 6 weeks | Screening + AML + Investigation |
| Phase 3: Clearing | 8 weeks | Adapters + Accounting + Saga |
| Phase 4: Operations | 4 weeks | Reporting + Monitoring + Hardening |

## Design Artifacts

| Document | Location |
|---|---|
| Architecture (interactive) | `docs/Design/payment-architecture.html` |
| Flow Diagram (interactive) | `docs/Design/payment-flow-diagram.html` |
| Coding Standards | Brain dump 002 / to be formalized |
| Clearing House Matrix | In architecture HTML (Section 02) |

---

*This brief will be formalized into APP_PRD.md once requirements gathering is complete.*
