# Payment House - Changelog

All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/).

---

## [Unreleased]

### 2026-02-08 — Training Program Plan (Viceral Academy)

- **Added:** Comprehensive training program plan (`docs/Design/TRAINING-PROGRAM-PLAN.md`)
- **Added:** 4-level certification track: VCPF → VCPE → VCPSA → VCPA (44 modules, 32 weeks)
- **Added:** Curriculum covering all Payment House technologies and domain knowledge
- **Added:** App design concept — dark theme, 5 key screens (dashboard, module, video, exam, certificate)
- **Added:** Video sourcing strategy — YouTube, Confluent, Spring Academy, Redis University, etc.
- **Added:** Exam format — MCQ, scenario, code reading, architecture, design questions
- **Added:** Implementation phases for the training app (MVP in 2-3 weeks)

### 2026-02-08 — Project Initialized + Architecture Design Ingested

- **Added:** Project scaffolding — docs structure, templates, gitignore
- **Added:** DEV-CLOCK time tracking (Step 1 complete)
- **Added:** Brain dump 001 — System Architecture (from Desktop session)
- **Added:** Brain dump 002 — Coding Standards & Design Patterns (from Desktop session)
- **Added:** Design Brief (`docs/Design/DESIGN-BRIEF.md`) — distilled from both sessions
- **Added:** Interactive architecture diagram (`docs/Design/payment-architecture.html`)
- **Added:** Interactive flow diagram (`docs/Design/payment-flow-diagram.html`)
- **Decided:** Tech stack — Java 21, Spring Boot, Kafka, PostgreSQL+Citus, ClickHouse, Redis, K8s, Istio (ADR-001)
- **Decided:** Architecture — Hexagonal + Event Sourcing + DDD + Saga (ADR-002)
- **Decided:** Multi-region — Single image, config-driven adapters, atomic pipeline (ADR-003)
- **Added:** LAUNCHPAD status block in README
- **Added:** Project rules in `.claude/CLAUDE.md` — filing workflow, document hierarchy, phase gates, changelog enforcement

---

## Changelog Format

Each entry follows:
```
### YYYY-MM-DD — Short Description
- **Added:** New features, files, capabilities
- **Changed:** Modifications to existing things
- **Decided:** Architecture/tech decisions made (links to ADR)
- **Removed:** Things taken out
- **Fixed:** Bug fixes
```
