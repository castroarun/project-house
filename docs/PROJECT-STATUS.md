# Payment House - Project Status

**Project:** Payment House (PayoneX)
**Tracking:** Klarity Dashboard
**Started:** 2026-02-08

---

## Current Project Status (9-Step Workflow)

| Step | Name | Status | Notes |
|------|------|--------|-------|
| 1 | DEV-CLOCK | Done | Time tracking initialized |
| 2 | PRD & Design | In Progress | Architecture, flows, training program, branding — all designed. PRD needs formalization |
| 3 | Test Cases | Not Started | |
| 4 | Build | Not Started | Phase 1: Foundation (8 weeks) |
| 5 | Manual Testing | Not Started | |
| 6 | Debug & Feedback | Not Started | |
| 7 | Code Walkthrough | Not Started | |
| 8 | Ship | Not Started | |
| 9 | Time Retrospective | Not Started | |

---

## Summary of What's Done

| Phase | Item | Status | Notes |
|-------|------|--------|-------|
| Setup | Project scaffolding | Done | Full docs structure |
| Setup | DEV-CLOCK | Done | Time tracking ready |
| Design | System Architecture | Done | 6-tier Kafka-driven microservices |
| Design | Coding Standards | Done | SOLID + CUPID + financial disciplines |
| Design | Tech Stack Decision | Done | Java 21, Kafka, PG+Citus, K8s (ADR-001) |
| Design | Architecture Pattern | Done | Hexagonal + Event Sourcing + DDD (ADR-002) |
| Design | Multi-Region Strategy | Done | Config-driven adapters (ADR-003) |
| Design | Compliance Saga | Done | Internal Async Saga — 4 parallel engines (ADR-004) |
| Design | Interactive Architecture Diagram | Done | [Live](https://castroarun.github.io/project-house/docs/Design/payment-architecture.html) |
| Design | Payment Flow Diagram | Done | [Live](https://castroarun.github.io/project-house/docs/Design/payment-flow-diagram.html) |
| Design | Flow Visualizations (4 variants) | Done | Swimlane, Circuit Board, Isometric, Metro Map |
| Design | Metro Map (Inbound + Outbound) | Done | Embedded in architecture page + [Standalone](https://castroarun.github.io/project-house/docs/Design/flow-metro-map.html) |
| Design | PayoneX Branding | Done | Name, logo, color tokens, all pages updated |
| Design | Design Brief | Done | High-level vision document |
| Design | Clearing House Matrix | Done | SG, HK, UK, IN configs documented |
| Design | pacs.002 Two-Stage Model | Done | ACTC (<500ms) + ACSC (varies by rail) |
| Design | Phantom Simulator | Done | Mock clearing house for dev/testing |
| Training | Training Program Plan | Done | 44 modules, 4 cert levels, 32 weeks |
| Training | PayArk Skill Tree Visualizations | Done | 4 variants (D3, CSS, Hybrid, Cytoscape) |
| Training | PayArk Academy App (M01 MVP) | Done | Next.js app, Supabase auth, live at [payark-academy](https://github.com/castroarun/payark-academy) |
| Marketing | LinkedIn Post 1 (PayoneX Architecture) | Done | Draft ready |
| Marketing | LinkedIn Post 2 (PayArk Academy) | Done | Draft ready |
| Design | PRD Document | In Progress | Needs formalization from design brief |

---

## Live GitHub Pages Links

### PayoneX Architecture & Design

| Page | Link |
|------|------|
| Architecture Diagram | [payment-architecture.html](https://castroarun.github.io/project-house/docs/Design/payment-architecture.html) |
| Payment Flow Diagram | [payment-flow-diagram.html](https://castroarun.github.io/project-house/docs/Design/payment-flow-diagram.html) |
| Flow — Swimlane | [flow-swimlane.html](https://castroarun.github.io/project-house/docs/Design/flow-swimlane.html) |
| Flow — Circuit Board | [flow-circuit-board.html](https://castroarun.github.io/project-house/docs/Design/flow-circuit-board.html) |
| Flow — Isometric | [flow-isometric.html](https://castroarun.github.io/project-house/docs/Design/flow-isometric.html) |
| Flow — Metro Map | [flow-metro-map.html](https://castroarun.github.io/project-house/docs/Design/flow-metro-map.html) |
| PayoneX Brand Variants | [payonex-brand-variants.html](https://castroarun.github.io/project-house/docs/Design/payonex-brand-variants.html) |

### PayArk Training Skill Trees

| Page | Link |
|------|------|
| Skill Tree — Hybrid (Recommended) | [payark-skilltree-hybrid.html](https://castroarun.github.io/project-house/docs/Design/payark-skilltree-hybrid.html) |
| Skill Tree — D3.js | [payark-skilltree-d3.html](https://castroarun.github.io/project-house/docs/Design/payark-skilltree-d3.html) |
| Skill Tree — Pure CSS | [payark-skilltree-css.html](https://castroarun.github.io/project-house/docs/Design/payark-skilltree-css.html) |
| Skill Tree — Cytoscape | [payark-skilltree-cytoscape.html](https://castroarun.github.io/project-house/docs/Design/payark-skilltree-cytoscape.html) |

---

## Architecture Decision Records

| ADR | Title | Status |
|-----|-------|--------|
| ADR-001 | Tech Stack Selection | Accepted |
| ADR-002 | Hexagonal Architecture + Event Sourcing | Accepted |
| ADR-003 | Configuration-Driven Multi-Region Strategy | Accepted |
| ADR-004 | Internal Async Saga for Compliance Screening | Accepted |

---

## Related Repos

| Repo | Purpose | Status |
|------|---------|--------|
| [project-house](https://github.com/castroarun/project-house) | PayoneX — architecture, design, docs | Active |
| [payark-academy](https://github.com/castroarun/payark-academy) | PayArk Academy — training app (M01 live) | Active |

---

## Next Actions

- [ ] Formalize APP_PRD.md from Design Brief
- [ ] Define detailed data model per bounded context
- [ ] Create API design document
- [ ] Deploy PayArk Academy to Vercel
- [ ] Set up development environment (Java 21, Kafka local, Docker Compose)
- [ ] Begin Phase 1: Foundation (Kafka cluster + Ingestion Gateway)

---

**Document Version:** 2.0
**Last Updated:** 2026-02-25
