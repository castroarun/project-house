# Payonex - Development Plan

**Status:** Pending (waiting for PRD approval)
**Last Updated:** 2026-02-21

---

## Tech Stack (Decided — see ADR-001)

| Layer | Technology | Reason |
|-------|-----------|--------|
| Language | Java 21 (Virtual Threads) | High throughput, mature ecosystem, banking standard |
| Framework | Spring Boot 3.3+ | Convention over config, production-ready |
| Event Streaming | Apache Kafka 3.7+ | Event sourcing backbone, source of truth |
| Primary DB | PostgreSQL 16 + Citus | ACID compliance, horizontal sharding via Citus |
| Cache | Redis Cluster 7.2+ | Low-latency lookups, session/rate-limit store |
| Analytics | ClickHouse | Column-oriented, fast aggregations for reporting |
| CDC/Outbox | Debezium 2.5+ | Transactional outbox pattern, change data capture |
| Orchestration | Kubernetes (EKS/GKE) | Container orchestration, auto-scaling |
| Service Mesh | Istio 1.21+ | mTLS, traffic management, observability |
| Secrets | HashiCorp Vault | Secrets management, dynamic credentials |
| Config | Consul / etcd | Distributed config, service discovery |
| Observability | Prometheus + OpenTelemetry + Grafana | Metrics, tracing, dashboards |
| CI/CD | GitLab CI + ArgoCD | Pipeline automation, GitOps deployment |

---

## Architecture

See `docs/Design/DESIGN-BRIEF.md` for full architecture. Summary:

**Kafka-driven, event-sourced microservices** — Hexagonal Architecture + DDD + Saga Pattern, organized into 6 tiers (Ingestion → Processing → Compliance → Clearing → Accounting → Reporting).

---

## Build Phases

| Phase | Scope | Estimated Time |
|-------|-------|----------------|
| Phase 0 — Proof of Concept | Throwaway spike, validate Kafka + event sourcing + single payment flow | 2-3 weeks |
| Phase 1 — Foundation | Kafka cluster + Ingestion Gateway + Message Processing | 8 weeks |
| Phase 2 — Compliance | Screening + AML + Fraud + Investigation workflows | 6 weeks |
| Phase 3 — Clearing | Country adapters + Accounting + Saga orchestration | 8 weeks |
| Phase 4 — Operations | Reporting + Monitoring + Hardening + SLA validation | 4 weeks |

---

## Dependencies

| Dependency | Purpose | Status |
|------------|---------|--------|
| Java 21 JDK | Runtime | Available |
| Docker Desktop / Rancher | Local container runtime | Available |
| K3s / minikube | Local Kubernetes | To install |
| Apache Kafka (Confluent Platform or Strimzi) | Event streaming | To install |
| PostgreSQL 16 + Citus extension | Primary database | To install |
| Redis 7.2+ | Cache layer | To install |
| ClickHouse | Analytics DB | To install |
| Debezium | CDC connector for Kafka | To install |
| Prometheus + Grafana | Observability stack | To install |

---

## Development Hardware & Infrastructure

### Context

Payonex runs a heavy stack locally — Kafka brokers, PostgreSQL+Citus, Redis, ClickHouse, multiple Spring Boot microservices on Kubernetes, plus the full observability pipeline. The development environment is in **Chennai, India**, where power outages (scheduled and unscheduled) are a regular concern.

The same machine also serves as a daily driver for movies, YouTube, VS Code with Claude AI, and trading.

### Minimum Specifications

| Component | Minimum | Ideal | Why |
|-----------|---------|-------|-----|
| **CPU** | 12+ cores, H-series mobile | 16+ cores (Ryzen 9 / i9 H-series) | Kafka + K8s + multiple JVMs are CPU-hungry |
| **RAM** | **64 GB DDR5** | 64-128 GB DDR5 | Kafka brokers (8 GB), PostgreSQL (8 GB), Redis (4 GB), ClickHouse (4 GB), 6+ JVMs (2-4 GB each), K8s overhead, IDE + browser |
| **Storage** | 1 TB NVMe Gen4 + empty 2nd M.2 slot | 2 TB NVMe Gen4 | Kafka logs + DB writes = heavy sequential I/O; must be NVMe, not SATA |
| **Display** | 15.6" 1080p IPS | 16" 1440p+ IPS or OLED | Trading charts + VS Code + movies need real estate |
| **Ports** | USB-C, HDMI | USB-C PD, HDMI 2.1, Ethernet/dongle | External monitor for trading + coding |
| **Battery** | 80+ Wh | 90+ Wh | Built-in UPS for Chennai power cuts |
| **GPU** | Integrated is fine | Dedicated (for display output) | Backend workload, no ML/GPU compute needed |

**Critical:** RAM must be in **2x SODIMM slots (upgradeable)**, not soldered. This eliminates most thin ultrabooks.

### Laptop Recommendations

#### Tier 1: Workstation Laptops (Best for sustained heavy loads)

| Laptop | CPU | RAM | Storage | Display | Price (INR approx) |
|--------|-----|-----|---------|---------|---------------------|
| **Lenovo ThinkPad P16 Gen 2** | i9-13980HX (24 cores) | 64 GB (upgradeable to 128) | 2 TB NVMe | 16" 2560x1600 IPS | 2.5-3.5L |
| **Dell Precision 7680** | i9-13950HX | 64 GB (upgradeable to 128) | 2 TB NVMe | 16" 2560x1600 | 2.5-3.5L |
| **HP ZBook Fury 16 G10** | i9-13950HX | 64 GB (upgradeable to 128) | 2 TB NVMe | 16" 1920x1200 | 2.5-3L |

**Why workstation class?** Better thermal design for sustained loads (running Kafka + 6 microservices for hours without throttling), ECC RAM support, superior keyboards, and ISV-certified for development tools.

#### Tier 2: Performance Laptops (Budget-friendly, upgrade yourself)

| Laptop | CPU | RAM | Storage | Display | Price (INR approx) |
|--------|-----|-----|---------|---------|---------------------|
| **ASUS ProArt Studiobook 16** | Ryzen 9 7945HX (16 cores) | 64 GB (2 slots) | 2 TB NVMe | 16" 3200x2000 OLED | 2-2.5L |
| **Lenovo Legion Pro 5 16"** | Ryzen 9 7945HX | 32 GB (upgrade to 64 GB) | 1 TB (add 2nd SSD) | 16" 2560x1600 240Hz | 1.5-2L |
| **MSI Creator 16** | i9-13980HX | 64 GB (2 slots) | 2 TB | 16" QHD+ | 2-2.5L |

**Buy the Legion Pro 5 with 32 GB and upgrade to 64 GB DDR5 yourself** (~INR 8-10K for a SODIMM kit) to save significantly.

#### Tier 3: MacBook Option

| Laptop | Chip | RAM | Storage | Price (INR approx) |
|--------|------|-----|---------|---------------------|
| **MacBook Pro 16" M4 Pro** | M4 Pro (14-core) | 48 GB unified | 1 TB | 2.8-3L |
| **MacBook Pro 16" M4 Max** | M4 Max (16-core) | 64 GB unified | 1 TB | 4-4.5L |

**Pros:** 15+ hour battery (survives any Chennai outage), silent, excellent display, Docker runs well.
**Cons:** ARM architecture — 95% of Java/Kafka/K8s stack works natively, but occasional x86-only container images need Rosetta emulation. RAM is **not upgradeable** — buy what you need upfront. 48 GB may be tight for the full stack.

### Power Protection Strategy (Chennai)

Chennai power outages are frequent — scheduled (1-2 hrs) and unscheduled (monsoon/transformer failures, potentially hours).

**With a laptop, the machine itself is a built-in UPS** (1-3 hours on battery depending on load). The only external devices needing protection are the router, switch, and external monitor.

#### Recommended Setup

```
Mains Power
  └─→ Laptop charger (battery handles 1-3 hr outages)
  └─→ Small UPS (600-1000VA) for router + external monitor + switch
```

| Item | Purpose | Cost (INR approx) |
|------|---------|---------------------|
| Router UPS (12V mini UPS) | Keeps internet alive during outages | 2-3K |
| Small UPS (600VA) for external monitor + peripherals | Prevents abrupt display loss | 3-5K |
| **Total power protection** | | **~5-8K** |

Compare this to a desktop workstation setup which would need INR 60K+ (inverter + online UPS).

#### Software-Level Data Protection

Even with battery power, always configure for unclean shutdown resilience:

| Service | Setting | Purpose |
|---------|---------|---------|
| Kafka | `acks=all`, `log.flush.interval.messages=1` (dev only) | Prevent message loss |
| PostgreSQL | `fsync=on`, `synchronous_commit=on` (defaults) | WAL integrity |
| Redis | `appendonly yes`, `appendfsync everysec` | AOF persistence |
| NVMe SSD | Buy a drive with **PLP (Power Loss Protection)** | Prevents write corruption on sudden power loss |
| Auto-recovery | Systemd/script to bring up Docker → Kafka → DB → services in order on boot | Clean restart after outage |

### Budget Summary

| Option | Hardware | Power Protection | Total (INR approx) |
|--------|----------|------------------|---------------------|
| **Budget (Legion Pro 5 + self-upgrade)** | 1.5-2L | 5-8K | **~1.6-2.1L** |
| **Mid-range (ProArt / ThinkPad P16)** | 2.5-3L | 5-8K | **~2.6-3.1L** |
| **Premium (MacBook Pro M4 Max)** | 4-4.5L | 3K (router UPS only) | **~4-4.5L** |

### Recommendation

**Best value:** Lenovo Legion Pro 5 16" (Ryzen 9) — buy base config, upgrade RAM to 64 GB DDR5 and add a 2nd NVMe SSD yourself. Total ~INR 1.7L. Handles the full Payonex stack + daily use comfortably.

**Best overall:** Lenovo ThinkPad P16 Gen 2 — if budget allows, the workstation-class thermals and build quality justify the premium for long sustained dev sessions.

---

*This document will be fully populated after Step 2 (PRD & Design) is complete.*
