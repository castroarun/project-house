<h1 align="center">Payonex</h1>

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
  "stage": "building",
  "progress": 25,
  "complexity": "F",
  "lastUpdated": "2026-02-25",
  "targetDate": null,
  "nextAction": "Formalize PRD, begin Phase 1 build",
  "blocker": null,
  "demoUrl": "https://castroarun.github.io/project-house/docs/Design/payment-architecture.html",
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

## Live Design Pages

Interactive HTML visualizations hosted via GitHub Pages:

| Page | Description |
|------|-------------|
| [Architecture Diagram](https://castroarun.github.io/project-house/docs/Design/payment-architecture.html) | Full 6-tier system architecture with inbound/outbound flows, metro maps, SLAs |
| [Payment Flow](https://castroarun.github.io/project-house/docs/Design/payment-flow-diagram.html) | End-to-end payment processing flow |
| [Metro Map](https://castroarun.github.io/project-house/docs/Design/flow-metro-map.html) | Transit-style payment flow (inbound FAST) |
| [Swimlane Flow](https://castroarun.github.io/project-house/docs/Design/flow-swimlane.html) | Cross-tier swimlane diagram |
| [Circuit Board](https://castroarun.github.io/project-house/docs/Design/flow-circuit-board.html) | PCB-style payment routing |
| [Isometric Flow](https://castroarun.github.io/project-house/docs/Design/flow-isometric.html) | 3D isometric architecture view |
| [PayArk Skill Tree](https://castroarun.github.io/project-house/docs/Design/payark-skilltree-hybrid.html) | 44-module training curriculum visualization |

---

## Project Structure

```
payment-house/
├── docs/
│   ├── brain-dump/                         # Desktop ideation session captures
│   ├── Design/
│   │   ├── DESIGN-BRIEF.md                 # High-level vision (evolving)
│   │   ├── APP_PRD.md                      # Product Requirements (formal)
│   │   ├── TRAINING-PROGRAM-PLAN.md        # PayArk 44-module curriculum
│   │   ├── payment-architecture.html       # Interactive architecture (+ metro maps)
│   │   ├── payment-flow-diagram.html       # Payment flow diagram
│   │   ├── flow-swimlane.html              # Swimlane flow
│   │   ├── flow-circuit-board.html         # Circuit board flow
│   │   ├── flow-isometric.html             # Isometric 3D flow
│   │   ├── flow-metro-map.html             # Metro map flow (standalone)
│   │   ├── payonex-brand-variants.html     # Brand identity variants
│   │   ├── payark-skilltree-hybrid.html    # PayArk skill tree (hybrid)
│   │   ├── payark-skilltree-d3.html        # PayArk skill tree (D3.js)
│   │   ├── payark-skilltree-css.html       # PayArk skill tree (CSS)
│   │   ├── payark-skilltree-cytoscape.html # PayArk skill tree (Cytoscape)
│   │   └── decisions/
│   │       ├── ADR-001-tech-stack.md
│   │       ├── ADR-002-architecture-pattern.md
│   │       ├── ADR-003-multi-region-strategy.md
│   │       └── ADR-004-compliance-saga.md
│   ├── CHANGELOG.md                        # Project changelog
│   ├── DEV-CLOCK.md                        # Time tracking
│   ├── DEVELOPMENT-PLAN.md                 # Technical plan
│   ├── GLOSSARY.md                         # Domain terminology (35+ terms)
│   ├── PROJECT-STATUS.md                   # 9-step workflow tracker
│   ├── linkedin-post-payonex-architecture.md  # LinkedIn Post 1
│   ├── linkedin-post-payark-academy.md        # LinkedIn Post 2
│   └── TEST-PLAN.csv                       # Test matrix
└── inits_n_info/
    └── requirements.md                     # Structured requirements
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
- [x] Architecture Decision Records (ADR-001 through ADR-004)
- [x] Interactive architecture & flow visualizations (7 HTML pages)
- [x] PayoneX branding and identity
- [x] PayArk training program (44 modules, 4 cert levels)
- [x] PayArk Academy app — Module 1 MVP ([repo](https://github.com/castroarun/payark-academy))
- [x] LinkedIn content (2 post drafts)
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
