# Payment House — Training Program Plan

**App Name:** PayForge
**Tagline:** _From Zero to Payment Architect_
**Status:** Plan (not yet built)
**Last Updated:** 2026-02-08

---

## 1. Program Overview

### What Is This?

A structured, self-paced training program that takes a developer from "I don't understand any of this" to "I can design and build an enterprise payment platform." Modeled after professional certification tracks (AWS SA, Confluent Kafka, Spring Certified) but tailored specifically to the Payment House architecture.

### Who Is This For?

- **Primary:** You (the builder) — to systematically learn every concept in the architecture before/while building it
- **Secondary:** Any developer joining this project who needs to ramp up
- **Tertiary:** Portfolio showcase — a learning platform is itself a portfolio piece

### Learning Philosophy

| Principle | Description |
|-----------|-------------|
| **Build to learn** | Every module ends with a hands-on mini-project, not just quizzes |
| **Layered depth** | Foundation → Intermediate → Advanced. No skipping |
| **Domain-first** | Learn payment concepts before the tech that implements them |
| **One concept, one module** | Each module teaches exactly one thing well |
| **Spaced repetition** | Key concepts resurface across modules in new contexts |

---

## 2. Program Structure

### Certification Tracks (4 Levels)

```
Level 1: Payment Foundations          (Beginner — 6 weeks)
Level 2: Platform Engineer            (Intermediate — 8 weeks)
Level 3: Payment Systems Architect    (Advanced — 10 weeks)
Level 4: Capstone — Build Payment House (Project — 8 weeks)
```

Each level has its own certificate. Completing all 4 earns the **PayForge Certified Payment Architect (VCPA)** designation.

---

### Level 1: Payment Foundations (6 weeks, 12 modules)

_Goal: Understand the payment domain, Java 21 fundamentals, and core design principles._

| Wk | Module | Title | Topics | Hands-On |
|----|--------|-------|--------|----------|
| 1 | M01 | How Payments Work | Payment lifecycle, clearing vs settlement, RTGS vs DNS, correspondent banking, nostro/vostro | Map a real SWIFT MT103 message field by field |
| 1 | M02 | ISO 20022 Decoded | MX messages, pain.001, pacs.008, pacs.002, XML schema, MT→MX migration | Parse a real pacs.008 XML, extract key fields |
| 2 | M03 | Clearing Houses Around the World | MEPS+, FAST, CHATS, FPS, CHAPS, RTGS India, NEFT, UPI, SWIFT gpi. Operating hours, cutoffs, thresholds | Build a clearing house config matrix from scratch |
| 2 | M04 | Compliance & Screening | Sanctions (OFAC/EU/UN), AML, PEP, fraud detection, investigation workflows, STR reporting | Design a screening decision tree for a sample payment |
| 3 | M05 | Java 21 for Payment Systems | Records, sealed classes, virtual threads, pattern matching, BigDecimal (mandatory), immutability | Refactor a mutable Payment class to immutable Java record |
| 3 | M06 | SOLID Principles (Applied) | SRP, OCP, LSP, ISP, DIP — all with payment domain examples | Identify SOLID violations in a sample payment codebase |
| 4 | M07 | CUPID + Financial Disciplines | Predictability, domain alignment, defensive calculations, auditability | Write a routing decision that carries its own audit trail |
| 4 | M08 | Design Patterns I — Strategy & Template | Strategy pattern (clearing adapters), Template Method (processing pipeline) | Build a mini clearing adapter system with 3 adapters |
| 5 | M09 | Design Patterns II — Specification & State Machine | Composable business rules, payment state machine, guard conditions | Implement a payment state machine with valid transitions |
| 5 | M10 | Hexagonal Architecture | Ports & adapters, domain isolation, zero framework imports in domain/ | Restructure a Spring app into hexagonal layers |
| 6 | M11 | Domain-Driven Design | Bounded contexts, aggregates, entities, value objects, ubiquitous language | Map the 6 Payment House bounded contexts |
| 6 | M12 | Twelve-Factor App | Config in env, stateless processes, port binding, dev/prod parity, logs as streams | 12-factor compliance audit on a sample app |

**Level 1 Exam:** 60 questions, 90 minutes. Pass: 70%.
**Certificate:** PayForge Certified — Payment Foundations (VCPF)

---

### Level 2: Platform Engineer (8 weeks, 16 modules)

_Goal: Master Kafka, databases, Spring Boot, and core microservices patterns._

| Wk | Module | Title | Topics | Hands-On |
|----|--------|-------|--------|----------|
| 1 | M13 | Apache Kafka Fundamentals | Producers, consumers, consumer groups, partitions, replication, retention | Set up Kafka locally, produce/consume payment messages |
| 1 | M14 | Kafka Deep Dive | Exactly-once semantics, transactions, idempotent producers, compaction, topic design | Design the 10 Payment House Kafka topics |
| 2 | M15 | Kafka Streams & Real-Time | Stream processing, materialized views, windowing, aggregations | Build a real-time payment volume dashboard from Kafka Streams |
| 2 | M16 | Spring Boot for Payment Systems | Profiles, externalized config, actuator, health checks, dependency injection | Multi-profile Spring app with region-specific configs |
| 3 | M17 | Spring Kafka Integration | Spring Kafka listeners, producers, error handlers, DLQ routing | End-to-end Kafka producer/consumer with retry |
| 3 | M18 | PostgreSQL for Finance | ACID, isolation levels, partitioning, indexing, pg_stat_statements | Design the payment_master schema with monthly partitions |
| 4 | M19 | Citus — Horizontal Sharding | Distributed PostgreSQL, shard key selection, distributed queries | Shard the ledger_db by account ID |
| 4 | M20 | Redis for Payment Systems | Caching, deduplication (TTL 7d), idempotency store, pub/sub | Build a Redis-backed deduplication gateway |
| 5 | M21 | ClickHouse Analytics | Columnar storage, MergeTree, materialized views, aggregation queries | Load 1M payment records, write analytical queries |
| 5 | M22 | Transactional Outbox + Debezium | CDC, WAL capture, outbox table design, exactly-once to Kafka | Implement outbox pattern with Debezium + PostgreSQL |
| 6 | M23 | Event Sourcing in Practice | Immutable events, event store, state reconstruction, snapshots | Build an event-sourced payment aggregate |
| 6 | M24 | Saga Pattern — Distributed Transactions | 5-step accounting saga, compensating transactions, saga log | Implement the accounting saga with failure compensation |
| 7 | M25 | Anti-Corruption Layer | Per clearing house ACL, external format translation, domain protection | Build ACL for a simulated SWIFT response format |
| 7 | M26 | Circuit Breaker & Resilience | Resilience4j, 3-state breaker, 3-tier DLQ, retry with backoff, bulkhead | Simulate clearing house failures with circuit breaker recovery |
| 8 | M27 | REST & gRPC API Design | API Gateway, rate limiting, protocol translation, Protobuf | Build a dual REST/gRPC payment submission API |
| 8 | M28 | Testing Strategies | Unit (AAA), integration (Testcontainers), contract, E2E, chaos, performance | Write test suites for a clearing adapter with >90% coverage |

**Level 2 Exam:** 80 questions, 120 minutes. Pass: 70%.
**Certificate:** PayForge Certified — Platform Engineer (VCPE)

---

### Level 3: Payment Systems Architect (10 weeks, 16 modules)

_Goal: Master infrastructure, observability, multi-region, security, and system design._

| Wk | Module | Title | Topics | Hands-On |
|----|--------|-------|--------|----------|
| 1 | M29 | Docker for Payment Microservices | Multi-stage builds, single image strategy, optimization, Docker Compose | Dockerize 3 payment microservices + Kafka + PG |
| 1 | M30 | Kubernetes Fundamentals | Pods, Deployments, Services, ConfigMaps, Secrets, HPA, PDB | Deploy payment services to a local K8s cluster |
| 2 | M31 | Kubernetes Advanced | StatefulSets (Kafka), network policies, RBAC, resource limits, affinity | Production-grade K8s manifests for Payment House |
| 2 | M32 | Istio Service Mesh | mTLS, traffic management, canary deployments, fault injection, Kiali | Canary deploy a clearing adapter with 95/5 traffic split |
| 3 | M33 | HashiCorp Vault | Dynamic secrets, auto-rotation, encryption-as-a-service, policies | Vault-managed database credentials for payment services |
| 3 | M34 | Consul / etcd for Config | Distributed config, hot-reload, service discovery, country configs | Hot-reload clearing house cutoff times without restart |
| 4 | M35 | Prometheus + Grafana | Custom metrics, PromQL, golden signals, alerting rules, Thanos | Build a Payment House operations dashboard |
| 4 | M36 | OpenTelemetry + Distributed Tracing | Span propagation, Jaeger, trace sampling, correlation IDs | Trace a payment end-to-end across 6 services |
| 5 | M37 | ELK Stack + Structured Logging | Structured JSON logs, MDC correlation ID, Filebeat, Logstash, Kibana | Centralized logging with payment correlation search |
| 5 | M38 | Self-Healing Infrastructure | K8s probes, anomaly detection, auto-scaling, DLQ auto-replay | Simulate failures, verify auto-recovery |
| 6 | M39 | Multi-Region Deployment | MirrorMaker 2, cross-region replication, RPO/RTO, DR failover | Set up 2-region Kafka replication with failover test |
| 7 | M40 | Security Architecture | TLS 1.3, field-level encryption, PII protection, RBAC, Kafka ACLs | Encrypt PII fields in payment messages with Vault KEKs |
| 8 | M41 | CI/CD Pipeline | GitLab CI, ArgoCD, GitOps, conventional commits, semantic versioning | Build a full CI/CD pipeline for a payment microservice |
| 9 | M42 | Performance Engineering | Load testing (Gatling/k6), p99 tuning, JVM optimization, connection pools | Load test the ingestion gateway to 10K msg/s |
| 10 | M43 | Regulatory Compliance & Reporting | LVT reports, STR filing, EOD reconciliation, 7-year archive, audit | Build an automated reconciliation engine |
| 10 | M44 | System Design — Payment Platform | Full system design exercise: whiteboard the complete Payment House | Design document: 6-tier architecture from scratch |

**Level 3 Exam:** 60 questions + 1 system design (written). 180 minutes. Pass: 75%.
**Certificate:** PayForge Certified — Payment Systems Architect (VCPSA)

---

### Level 4: Capstone — Build Payment House (8 weeks)

_Goal: Build a working subset of Payment House end-to-end._

| Wk | Sprint | Deliverable |
|----|--------|-------------|
| 1-2 | Sprint 1 | Kafka cluster + Ingestion Gateway with IBM MQ bridge + dedup |
| 3-4 | Sprint 2 | Message Processor + Enrichment + Payment Master DB |
| 5-6 | Sprint 3 | Compliance screening (mock) + Clearing adapter (1 country) + Circuit breaker |
| 7-8 | Sprint 4 | Accounting saga + Reporting dashboard + E2E test + Observability |

**Capstone Evaluation:** Working demo + architecture walkthrough + code review.
**Certificate:** PayForge Certified Payment Architect (VCPA)

---

## 3. Video Content Sourcing Strategy

### Approach: Curate First, Create Second

| Priority | Source | Type | Cost | Quality |
|----------|--------|------|------|---------|
| 1 | **YouTube (free)** | Curated playlists per module | Free | Variable — handpick best |
| 2 | **Udemy** | Full courses, cherry-pick sections | $10-15/course on sale | Good, structured |
| 3 | **Confluent Developer** | Official Kafka training | Free tier available | Excellent for Kafka |
| 4 | **Spring Academy** | Official Spring courses | Free + paid tiers | Best for Spring Boot |
| 5 | **Baeldung** | Java/Spring written tutorials + some video | Free + Pro | Best written Java content |
| 6 | **IBM Developer** | MQ, integration patterns | Free | Good for IBM MQ |
| 7 | **SWIFT** | ISO 20022, payment standards | Free learning portal | Authoritative |
| 8 | **HashiCorp Learn** | Vault, Consul tutorials | Free | Official, hands-on |
| 9 | **Kubernetes.io** | Official K8s tutorials | Free | Canonical |
| 10 | **Self-recorded** | Payment domain, architecture walkthroughs | Time investment | Custom, perfectly targeted |

### Recommended Curated Courses (per module cluster)

| Domain | Platform | Course / Channel | Notes |
|--------|----------|------------------|-------|
| Java 21 | YouTube | Amigoscode, Java Brains | Modern Java features |
| Spring Boot | Spring Academy | Spring Certified Professional prep | Official, free tier |
| Kafka | Confluent Developer | Kafka Fundamentals + Streams | Official, free, excellent |
| Kafka | Udemy | "Apache Kafka for Beginners" (Stephane Maarek) | Gold standard Kafka course |
| PostgreSQL | Udemy | "The Complete SQL Bootcamp" | Fundamentals |
| Citus | Citus Data (Microsoft) | Official tutorials | Free, niche |
| ClickHouse | ClickHouse Academy | Official training | Free |
| Redis | Redis University | RU101, RU201 | Free, official |
| DDD | YouTube | Milan Jovanovic, CodeOpinion | Excellent DDD content |
| Design Patterns | YouTube | Christopher Okhravi | Best pattern explanations |
| Hexagonal | YouTube | Tom Hombergs ("Get Your Hands Dirty on Clean Architecture") | Book + talks |
| Event Sourcing | YouTube | Greg Young (original talks) | Definitive source |
| Kafka Streams | Confluent Developer | Kafka Streams 101 | Free, official |
| Docker | YouTube | TechWorld with Nana | Clear, practical |
| Kubernetes | YouTube | TechWorld with Nana | Clear, practical |
| Istio | Istio.io | Official docs + Tetrate Academy | Free |
| Vault | HashiCorp Learn | Vault Getting Started | Official |
| Prometheus/Grafana | YouTube | TechWorld with Nana | Practical |
| ISO 20022 | SWIFT | ISO 20022 Learning | Industry standard |
| Payment Systems | YouTube | Payments Explained (various) | Curate best explainers |

### Video Sourcing Workflow

```
For each module:
1. Search YouTube for the topic — find 2-3 best free videos
2. Check if Confluent/Spring/Redis/HashiCorp has official training
3. If coverage is poor or too generic, flag for self-recording
4. Record custom videos only for Payment House–specific content
   (domain walkthroughs, architecture decisions, clearing house specifics)
```

---

## 4. App Design Concept

### App Name

**PayForge** — Builder energy, forging payment expertise. Premium, memorable, unique.

### Design Philosophy

```
Minimalist dark theme (like the architecture HTML diagrams you already built)
+ Progress tracking that feels like a game without being gamified
+ Zero clutter, maximum focus on content
```

### Key UI Screens

#### 1. Dashboard (Home)
```
┌─────────────────────────────────────────────────────────┐
│  PayForge                                 [avatar] [☀/🌙]│
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Welcome back, Arun                                     │
│                                                         │
│  ┌─────────────────────────────────────────────┐        │
│  │ CURRENT PATH                                │        │
│  │                                             │        │
│  │ Level 2: Platform Engineer                  │        │
│  │ Module 17: Spring Kafka Integration         │        │
│  │ ████████████░░░░░░░░ 58%                    │        │
│  │                                             │        │
│  │ [Continue Learning →]                       │        │
│  └─────────────────────────────────────────────┘        │
│                                                         │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐   │
│  │ Level 1  │ │ Level 2  │ │ Level 3  │ │ Capstone │   │
│  │ ✓ Done   │ │ 58%      │ │ Locked   │ │ Locked   │   │
│  │ VCPF     │ │ ████░░░░ │ │          │ │          │   │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘   │
│                                                         │
│  RECENT ACTIVITY                                        │
│  ○ Completed M16: Spring Boot for Payments   2h ago     │
│  ○ Passed Quiz: Kafka Partitioning           yesterday  │
│  ○ Earned badge: First Circuit Breaker       2 days ago │
│                                                         │
│  STATS                                                  │
│  Modules: 18/44    Hours: 62    Streak: 7 days          │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

#### 2. Module View
```
┌─────────────────────────────────────────────────────────┐
│  ← Level 2    M17: Spring Kafka Integration             │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  OVERVIEW                                               │
│  Learn to integrate Spring Boot with Apache Kafka for   │
│  payment message production and consumption with        │
│  error handling and DLQ routing.                        │
│                                                         │
│  Prerequisites: M13, M14, M16                           │
│  Estimated time: 4 hours                                │
│                                                         │
│  ┌─ CONTENT ─────────────────────────────────────────┐  │
│  │                                                   │  │
│  │  ▶ 1. Video: Spring Kafka Basics        (18 min)  │  │
│  │  ✓ 2. Reading: KafkaListener Deep Dive  (12 min)  │  │
│  │  ▶ 3. Video: Error Handling & DLQ       (22 min)  │  │
│  │  ○ 4. Hands-On Lab: Build Producer      (45 min)  │  │
│  │  ○ 5. Hands-On Lab: Build Consumer+DLQ  (45 min)  │  │
│  │  ○ 6. Quiz: 15 questions                (20 min)  │  │
│  │  ○ 7. Mini-Project: Payment Pipeline    (60 min)  │  │
│  │                                                   │  │
│  └───────────────────────────────────────────────────┘  │
│                                                         │
│  RESOURCES                                              │
│  [Spring Docs]  [Confluent Guide]  [Source Code]        │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

#### 3. Video Player View
```
┌─────────────────────────────────────────────────────────┐
│  ← M17    Spring Kafka Basics                           │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  ┌───────────────────────────────────────────────────┐  │
│  │                                                   │  │
│  │              [VIDEO PLAYER]                       │  │
│  │              16:9 aspect ratio                    │  │
│  │              Dark player chrome                   │  │
│  │                                                   │  │
│  │  ▶  ████████░░░░░░░░░░░░  7:32 / 18:14          │  │
│  │  [1x] [CC] [Notes] [Bookmark] [⛶]               │  │
│  └───────────────────────────────────────────────────┘  │
│                                                         │
│  ┌─ NOTES (auto-saved) ──────────────────────────────┐  │
│  │ - @7:32 KafkaListener uses consumer group ID      │  │
│  │ - Error handler can route to DLQ topic            │  │
│  │ - [+ Add note]                                    │  │
│  └───────────────────────────────────────────────────┘  │
│                                                         │
│  KEY CONCEPTS                                           │
│  [KafkaListener]  [ConsumerGroup]  [ErrorHandler]       │
│                                                         │
│  [← Previous]                    [Next: DLQ Routing →]  │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

#### 4. Exam View
```
┌─────────────────────────────────────────────────────────┐
│  EXAM: Level 2 — Platform Engineer         47:23 left   │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Question 34 of 80                                      │
│  ░░░░░░░░░░░░░░░████████████░░░░░░░░░░░░░░░░░░░░       │
│                                                         │
│  A payment message is stuck in SCREENING state and      │
│  the compliance engine is not responding. The circuit   │
│  breaker has moved to OPEN state.                       │
│                                                         │
│  What happens to incoming payments for this engine?     │
│                                                         │
│  ○ A) They are immediately rejected                     │
│  ● B) They are buffered in a Kafka retry topic          │
│  ○ C) They skip compliance and proceed to clearing      │
│  ○ D) They are routed to the DLQ                        │
│                                                         │
│  ┌─ CONFIDENCE ────────────────┐                        │
│  │ [Sure] [Guessing] [Flag]   │                        │
│  └────────────────────────────┘                        │
│                                                         │
│  [← Previous]  [Flag for Review]  [Next →]              │
│                                                         │
│  Progress: 12 answered · 3 flagged · 65 remaining       │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

#### 5. Certificate View
```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│                  ╔═══════════════════╗                   │
│                  ║     PAYFORGE      ║                   │
│                  ╚═══════════════════╝                   │
│                                                         │
│              Certificate of Achievement                 │
│                                                         │
│                    Arun Castro                           │
│                                                         │
│         has successfully completed Level 2              │
│                                                         │
│          PLATFORM ENGINEER (VCPE)                       │
│                                                         │
│     Score: 82%  |  Date: 2026-03-15                     │
│     Credential ID: VCPE-2026-00001                      │
│                                                         │
│     [Download PDF]  [Share on LinkedIn]  [Verify]       │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### UI Design Principles

| Principle | Implementation |
|-----------|---------------|
| **Dark theme default** | Matches Payment House architecture diagrams aesthetic |
| **Minimal chrome** | Content-first, toolbars only when needed |
| **Progress everywhere** | Subtle progress bars, never aggressive gamification |
| **Keyboard-first** | Arrow keys for navigation, space for play/pause, N for notes |
| **Responsive** | Works on mobile for reading, desktop for labs |
| **Offline capable** | PWA with service worker, downloaded content works offline |
| **Accessibility** | WCAG 2.1 AA, proper focus management, screen reader support |

### Design References

| Reference | What to Take |
|-----------|-------------|
| Linear.app | Minimal UI, dark theme, keyboard shortcuts |
| Stripe Docs | Clean typography, code blocks, navigation |
| Notion | Content hierarchy, sidebar navigation |
| Frontend Masters | Video player UX, progress tracking |
| Brilliant.org | Interactive learning elements |

---

## 5. Exam & Assessment Format

### Per-Module Quizzes
- **Format:** 10-15 multiple choice + code snippet questions
- **Time:** 15-20 minutes
- **Pass mark:** 70%
- **Retakes:** Unlimited (different question pool each time)
- **Purpose:** Checkpoint before moving to next module

### Level Certification Exams

| Exam | Questions | Time | Format | Pass |
|------|-----------|------|--------|------|
| Level 1: VCPF | 60 MCQ | 90 min | Multiple choice, scenario-based | 70% |
| Level 2: VCPE | 80 MCQ | 120 min | MCQ + code reading + architecture diagrams | 70% |
| Level 3: VCPSA | 60 MCQ + 1 design | 180 min | MCQ + written system design (open-ended) | 75% |
| Level 4: VCPA | Project evaluation | N/A | Working demo + code review + architecture walkthrough | Pass/Fail |

### Question Types

1. **Conceptual:** "What pattern should you use for distributed transactions in accounting?"
2. **Scenario:** "A payment is stuck in SUBMITTED state for 45 seconds. The clearing house SLA is 30s. What happens next?"
3. **Code reading:** "Given this Java code, identify the SOLID violation."
4. **Architecture:** "Given this system diagram, identify the single point of failure."
5. **Debugging:** "This Kafka consumer is processing duplicates. What's missing?"
6. **Design (Level 3 only):** "Design a new clearing adapter for SEPA. Document your approach."

### Question Pool Strategy
- Each module contributes 30-50 questions to the pool
- Exams randomly select from the pool
- Questions have difficulty tags (easy/medium/hard)
- Each exam guarantees a spread: 30% easy, 50% medium, 20% hard
- Pool grows over time — add questions as you learn more

---

## 6. Certification Names & Branding

### Certificates

| Level | Abbreviation | Full Name | Badge Color |
|-------|-------------|-----------|-------------|
| 1 | **VCPF** | PayForge Certified — Payment Foundations | Blue |
| 2 | **VCPE** | PayForge Certified — Platform Engineer | Cyan |
| 3 | **VCPSA** | PayForge Certified — Payment Systems Architect | Violet |
| 4 | **VCPA** | PayForge Certified Payment Architect | Gold |

### Digital Badges
- SVG badges for each level
- Verifiable credential IDs (VCPE-YYYY-NNNNN)
- LinkedIn-shareable (Open Badge standard)
- QR code linking to verification page

---

## 7. App Tech Stack (Proposed)

| Layer | Technology | Reason |
|-------|-----------|--------|
| Frontend | Next.js 14 + TypeScript | Your existing stack, fast, SSR |
| Styling | Tailwind CSS | Rapid development, dark theme |
| State | Zustand or React Context | Lightweight, no Redux overhead |
| Database | Supabase (PostgreSQL) | Auth + DB + storage in one |
| Auth | Supabase Auth | Google OAuth, email/password |
| Video Hosting | YouTube (embedded) or Bunny.net | Free (YT) or cheap CDN (Bunny) |
| Content | MDX files | Markdown + React components for lessons |
| Progress | Supabase tables | Module completion, quiz scores, streaks |
| Offline | PWA + Service Worker | Cache lessons for offline reading |
| Deployment | Vercel | Your existing platform |

### Why This Stack?
- You already know Next.js/TypeScript/Tailwind/Supabase from other projects
- Zero new infrastructure to learn just for the training app
- The training app itself becomes a portfolio piece
- Supabase handles auth, progress storage, and file storage in one

---

## 8. Content Creation Workflow

### For Each Module (in order)

```
1. OUTLINE    — Write learning objectives + topic list (10 min)
2. CURATE     — Find best YouTube/official videos (30 min)
3. READING    — Write 1-2 page reading material in MDX (45 min)
4. LAB        — Design hands-on exercise with starter code (60 min)
5. QUIZ       — Write 30-50 questions for the question pool (45 min)
6. REVIEW     — Test the module yourself end-to-end (30 min)
7. PUBLISH    — Push to app (10 min)
```

**Estimated time per module:** ~4 hours of content creation
**Total for 44 modules:** ~176 hours (spread over the build timeline)

### Content can be created incrementally
- Build Level 1 content while studying Level 1 topics
- Content creation IS the learning — writing quiz questions forces deep understanding

---

## 9. Implementation Phases

### Phase A: MVP App (2-3 weeks)
- Dark theme UI shell (dashboard, module list, video embed)
- Supabase auth (Google login)
- Module progress tracking (local + Supabase)
- Level 1 content: first 4 modules curated and published
- Basic quiz engine (MCQ only)

### Phase B: Full Learning Experience (2-3 weeks)
- All Level 1 modules published
- Notes feature (timestamped, per-video)
- Hands-on lab framework (CodeSandbox or StackBlitz embeds)
- Certificate generation (PDF)
- Level 1 exam engine

### Phase C: Scale Content (ongoing)
- Level 2, 3, 4 content published incrementally
- Question pool growing per module
- Performance dashboard (study time, strengths/weaknesses)
- LinkedIn badge sharing

### Phase D: Polish (2 weeks)
- PWA offline support
- Keyboard navigation
- Accessibility audit
- Mobile optimization
- Landing page for portfolio

---

## 10. Metrics & Success Criteria

| Metric | Target |
|--------|--------|
| Module completion rate | >80% of started modules completed |
| Quiz first-attempt pass rate | 60-80% (too high = too easy) |
| Average module time | Within 20% of estimated time |
| Daily streak engagement | Track but don't gamify aggressively |
| Level exam pass rate | 70-85% first attempt |
| Time to VCPA (all 4 levels) | 32 weeks (8 months) if full-time study |

---

## Appendix: Module → Payment House Component Mapping

Every module maps directly to a part of Payment House you'll build:

| Module Range | Payment House Component |
|-------------|------------------------|
| M01-M04 | Domain knowledge for all tiers |
| M05-M12 | Code quality for all services |
| M13-M15 | Kafka backbone (Tiers 1-6) |
| M16-M17 | Spring Boot services (all tiers) |
| M18-M19 | Databases (per-service) |
| M20 | Redis layer (Tier 1 dedup, idempotency) |
| M21 | ClickHouse (Tier 6 reporting) |
| M22 | Outbox pattern (all producers) |
| M23 | Event sourcing (all tiers) |
| M24 | Saga (Tier 5 accounting) |
| M25 | ACL (Tier 4 clearing adapters) |
| M26 | Resilience (Tier 4 circuit breakers) |
| M27 | API layer (Tier 1 ingestion) |
| M28 | Testing (all tiers) |
| M29-M32 | Infrastructure (K8s, Istio) |
| M33-M34 | Secrets & config (cross-cutting) |
| M35-M37 | Observability (cross-cutting) |
| M38 | Self-healing (cross-cutting) |
| M39 | Multi-region (deployment) |
| M40 | Security (cross-cutting) |
| M41 | CI/CD pipeline |
| M42 | Performance (SLA targets) |
| M43 | Regulatory (Tier 6 reporting) |
| M44 | System design (full architecture) |

---

*This is the plan. The app and content will be built separately.*
*Next step: Review this plan → decide app name → begin Phase A MVP.*
