<h1 align="center">Payment House</h1>

<h3 align="center">
  Enterprise Payment Processing Platform
</h3>

<p align="center">
  Kafka-driven, event-sourced microservices architecture for core banking payments across Singapore, Hong Kong, UK, and India.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-21-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring_Boot-3.3-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" />
  <img src="https://img.shields.io/badge/Apache_Kafka-3.7-231F20?style=for-the-badge&logo=apachekafka&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-16+Citus-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Kubernetes-EKS/GKE-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" />
  <img src="https://img.shields.io/badge/ISO_20022-Native-0078D4?style=for-the-badge" />
  <img src="https://img.shields.io/badge/License-Proprietary-red?style=for-the-badge" />
</p>

<!-- LAUNCHPAD:START -->
```json
{
  "stage": "idea",
  "progress": 10,
  "complexity": "F",
  "lastUpdated": "2026-02-08",
  "targetDate": null,
  "nextAction": "Formalize PRD from Design Brief",
  "blocker": null,
  "demoUrl": null,
  "techStack": ["Java 21", "Spring Boot", "Apache Kafka", "PostgreSQL", "Citus", "ClickHouse", "Redis", "Kubernetes", "Istio"],
  "shipped": false,
  "linkedinPosted": false
}
```
<!-- LAUNCHPAD:END -->

---

## Why Payment House

Modern payment processing requires handling dozens of clearing houses, each with unique protocols, operating hours, message formats, and regulatory requirements. Scaling across regions traditionally means maintaining separate codebases that drift apart.

Payment House solves this by:

- **Single codebase, config-driven regions** — One Docker image runs identically in Singapore, Hong Kong, UK, and India
- **Event sourcing as standard** — Every payment state change is an immutable event, enabling full audit trails, replay, and disaster recovery
- **Self-healing infrastructure** — Circuit breakers, 3-tier DLQ retry, anomaly detection, and auto-recovery handle 95% of incidents without human intervention

---

## Architecture

Six architectural tiers connected by Apache Kafka:

| Tier | Name | Responsibility |
|------|------|----------------|
| 1 | **Ingestion Gateway** | Multi-protocol entry (IBM MQ, SFTP, REST/gRPC, ISO 20022), deduplication |
| 2 | **Message Processing** | Schema validation, MT-to-MX conversion, BIC/IBAN/FX enrichment |
| 3 | **Compliance Screening** | Parallel sanctions (OFAC/EU/UN), AML, fraud ML, PEP screening |
| 4 | **Routing & Clearing** | Country-specific adapters: MEPS+, FAST, CHATS, FPS, SWIFT gpi |
| 5 | **Accounting & Settlement** | Double-entry ledger, 5-step Saga with compensating transactions |
| 6 | **Reporting & Recon** | Real-time dashboards, regulatory reports, EOD reconciliation |

### Clearing House Coverage

| Region | RTGS | Real-Time Retail | Batch |
|--------|------|------------------|-------|
| Singapore | MEPS+ (MAS) | FAST (ABS) | IBG |
| Hong Kong | HKD CHATS (HKICL) | FPS | Bulk BACS equiv. |
| United Kingdom | CHAPS (BoE) | Faster Payments (VocaLink) | BACS |
| India | RTGS (RBI) | UPI/IMPS (NPCI) | NEFT (48 batches/day) |
| Global | — | — | SWIFT gpi |

---

## Tech Stack

| Category | Technology | Version |
|----------|------------|---------|
| Language | Java (Virtual Threads) | 21 LTS |
| Framework | Spring Boot | 3.3+ |
| Event Streaming | Apache Kafka | 3.7+ |
| Primary Database | PostgreSQL + Citus | 16+ |
| Analytics | ClickHouse | 24.x |
| Cache | Redis Cluster | 7.2+ |
| CDC / Outbox | Debezium | 2.5+ |
| Orchestration | Kubernetes (EKS/GKE) | 1.29+ |
| Service Mesh | Istio | 1.21+ |
| Secrets | HashiCorp Vault | 1.16+ |
| Config | Consul / etcd | — |
| Observability | Prometheus + OTel + Grafana | — |
| CI/CD | GitLab CI + ArgoCD | — |

---

## Design Patterns

- **Hexagonal Architecture** (Ports & Adapters) — Domain isolated from infrastructure
- **Domain-Driven Design** — 6 bounded contexts with database-per-service
- **Event Sourcing** — Kafka log as source of truth
- **Saga Pattern** — 5-step accounting with compensating transactions
- **Strategy Pattern** — Pluggable clearing adapters discovered at runtime
- **Anti-Corruption Layer** — Per clearing house, isolates external protocol quirks
- **Circuit Breaker** — Resilience4j with 3-state (CLOSED/OPEN/HALF-OPEN)
- **Transactional Outbox** — Debezium CDC for exactly-once Kafka publishing

---

## Project Structure

```
payment-house/
├── docs/
│   ├── brain-dump/                    # Desktop ideation session captures
│   ├── Design/
│   │   ├── DESIGN-BRIEF.md            # High-level vision (evolving)
│   │   ├── APP_PRD.md                 # Product Requirements (formal)
│   │   ├── payment-architecture.html  # Interactive architecture diagram
│   │   ├── payment-flow-diagram.html  # Interactive flow diagram
│   │   └── decisions/
│   │       ├── ADR-001-tech-stack.md
│   │       ├── ADR-002-architecture-pattern.md
│   │       └── ADR-003-multi-region-strategy.md
│   ├── CHANGELOG.md                   # Project changelog
│   ├── DEV-CLOCK.md                   # Time tracking
│   ├── DEVELOPMENT-PLAN.md            # Technical plan
│   ├── GLOSSARY.md                    # Domain terminology (35+ terms)
│   ├── PROJECT-STATUS.md              # 9-step workflow tracker
│   └── TEST-PLAN.csv                  # Test matrix
└── inits_n_info/
    └── requirements.md                # Structured requirements
```

---

## SLA Targets

| Metric | Target | Alert Threshold |
|--------|--------|-----------------|
| FAST E2E (p99) | < 5 seconds | > 8 seconds |
| RTGS E2E (p99) | < 15 seconds | > 25 seconds |
| Ingestion throughput | 10K msg/s | < 5K msg/s |
| Kafka latency (p99) | < 10ms | > 50ms |
| DB OLTP (p95) | < 5ms | > 20ms |
| Availability | 99.99% | Any downtime |
| MTTD | < 30 seconds | — |
| MTTR (auto) | < 2 minutes | — |

---

## Roadmap

- [x] Project scaffolding and documentation structure
- [x] System architecture design (6-tier Kafka pipeline)
- [x] Coding standards and design patterns defined
- [x] Architecture Decision Records (ADR-001 through ADR-003)
- [ ] Formalize PRD from Design Brief
- [ ] Detailed data model per bounded context
- [ ] API design document
- [ ] Phase 1: Foundation — Kafka + Ingestion + Message Processing (8 weeks)
- [ ] Phase 2: Compliance — Screening + AML + Investigation (6 weeks)
- [ ] Phase 3: Clearing — Adapters + Accounting + Saga (8 weeks)
- [ ] Phase 4: Operations — Reporting + Monitoring + Hardening (4 weeks)

---

## Status

| Step | Phase | Status |
|------|-------|--------|
| 1 | DEV-CLOCK | Done |
| 2 | PRD & Design | In Progress |
| 3 | Test Cases | Not Started |
| 4-9 | Build through Ship | Not Started |

See [PROJECT-STATUS.md](docs/PROJECT-STATUS.md) for detailed progress.

---

<p align="center">
  <sub>Built by <a href="https://github.com/Castro-1">Castro</a></sub>
</p>
