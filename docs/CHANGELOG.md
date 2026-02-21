# Payment House - Changelog

All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/).

---

## [Unreleased]

### 2026-02-21 — PayoneX Branding Applied to HTML Pages
- **Changed:** Architecture HTML — hero title now **PayoneX** with "Enterprise Payment Processing Platform" as subtitle underneath
- **Changed:** Architecture HTML — page `<title>` set to "PayoneX — Enterprise Payment Processing Platform"
- **Changed:** Architecture HTML — footer updated to "PayoneX · Enterprise Payment Processing Platform · Architecture v2.0"
- **Changed:** Standalone metro map — header now shows **PayoneX** as h1 with "Enterprise Payment Processing Platform" subtitle and flow description below
- **Changed:** All "Payonex" references updated to **PayoneX** (capital X) across both HTML files

### 2026-02-21 — Metro Maps Embedded as Collapsible Sections
- **Changed:** Metro maps now shown as **collapsible accordions** below the L→R simple views (replaced toggle buttons)
- **Added:** Inbound metro map — collapsible below L→R, shows full transit diagram with trunk line, MQ/Kafka interchanges, dev callouts, ⚡ ACTC and ✓ ACSC icons
- **Added:** Outbound metro map — new transit diagram covering full outbound flow: Internal Channel → T1 → T2 Build → T3 Compliance → T5 Pre-Clearing Saga → T4 Clearing Adapter → MQ Out → FAST/Phantom → MQ In → T1 Response → T2 Correlate → T5 Post-Clearing Saga → T6 Reporting
- **Changed:** L→R simple views always visible for both inbound and outbound (no longer hidden behind toggle)
- **Changed:** L→R inbound view updated to match metro map flow — shows DBS → FAST → MQ → T1 → ACTC → Kafka → T2 → T3 → T5 → ACSC → T6 (no Tier 4 for inbound)
- **Added:** Collapsible UI — chevron arrow + METRO MAP badge, smooth expand/collapse animation
- **Added:** All metro map CSS scoped under `.mm` prefix to avoid conflicts with architecture page styles
- **Added:** Backup created at `payment-architecture.backup.html` before integration

### 2026-02-21 — Compliance Saga Pattern & Metro Map Refinements
- **Decided:** Compliance screening uses **Option A — Internal Async Saga** — all 4 engines (Sanctions, AML, Fraud, PEP) run as parallel tasks inside a single Tier 3 service, aggregator waits for all 4 futures, publishes single event to `payments.compliance.passed` (ADR-004)
- **Changed:** Metro map flow corrected — removed Tier 4 Clearing from inbound flow (clearing house is the SOURCE for inbound, not a processing step)
- **Added:** Metro map — Station 0 (Originating Bank / DBS) and Station 1 (Clearing House / FAST Network) as separate entry points
- **Added:** Metro map — Phantom dev simulation callout cards (orange dashed) for DBS and FAST stations
- **Added:** Metro map — IBM MQ interchange markers (blue) for `MQ.INBOUND.FAST.001` and `MQ.OUTBOUND.FAST.001`
- **Added:** Metro map — MQ return callout cards (blue, left-side) for ACTC and ACSC pacs.002 responses back to clearing house
- **Fixed:** Metro map — trunk line clipped to start/end at first/last station dots
- **Fixed:** Metro map — container width reverted to 900px (callouts are absolutely positioned)
- **Decided:** Internal MS-to-MS communication via Kafka; IBM MQ only at edges (external clearing house interface)
- **Decided:** Kafka chosen over RabbitMQ for audit trail (log retention), replay on failure, multiple consumers, payment ordering via partition key, event sourcing

### 2026-02-21 — Metro Map Payment Flow Visualization
- **Added:** `docs/Design/flow-metro-map.html` — standalone Metro Map / Transit Diagram visualization of the inbound FAST payment flow (DBS to Payonex)
- **Added:** 7 stations along a blue trunk line: External Origin, Tier 1 Ingestion, ACTC ACK, Tier 2 Processing, Tier 3 Compliance, Tier 4 Clearing, Tier 5 Accounting, ACSC Final, Tier 6 Reporting
- **Added:** Clearing branch diagram — trunk line splits into 5 color-coded routes (FAST/MEPS+/CHATS/FPS/SWIFT gpi) with SVG animations and SLA badges, then reconverges
- **Added:** Compliance parallel fan-out grid showing Sanctions, AML, Fraud, and PEP screening with SLA targets
- **Added:** Kafka interchange markers between each tier with topic names
- **Added:** ACTC (green glow) and ACSC (cyan glow) as special highlighted pacs.002 milestone stations
- **Added:** Animated pulse along trunk line, animated dots on clearing branch lines
- **Added:** Legend section with line color meanings

### 2026-02-21 — Inbound & Outbound Flow Visuals + Phantom Simulator
- **Added:** Architecture HTML — new Section 01a "Inbound Payment Flow" with full visual: FAST pacs.008 → Tier 1 → ACTC ACK (<500ms) → Tier 2 → Tier 3 compliance → Tier 5 accounting → ACSC final (<5s) → Tier 6 reporting
- **Added:** Architecture HTML — new Section 01b "Outbound Payment Flow" with full visual: internal instruction → Tier 1-3 → Pre-Clearing Saga (Part 1) → Tier 4 Clearing Adapter → PROD/DEV split → Tier 1 response → Tier 2 correlate → Post-Clearing Saga (Part 2) → Tier 6
- **Added:** Nav buttons for "Inbound Flow" and "Outbound Flow" in architecture HTML
- **Decided:** Mock clearing simulator named **Phantom** — standalone Docker container that simulates clearing house responses (pacs.002) for dev/testing, tests full round-trip through MQ → Tier 1 → Tier 2
- **Added:** Phantom callout in architecture HTML with design rationale and configurable scenarios (Success/ACSC, Rejection/RJCT, Timeout, Partial, Network error)

### 2026-02-21 — Two-Stage pacs.002 Model & SLA Refinement
- **Changed:** Architecture HTML Section 11 — Production Targets now show two-stage pacs.002 model: ACK (ACTC <500ms, all rails) + Final (ACSC: <5s real-time, <15s RTGS, <35s cross-border)
- **Changed:** Architecture HTML Section 11 — Dev environment pacs.002 SLA card updated to reflect ACK (ACTC <500ms)
- **Changed:** Clarified pacs.002 staging varies by clearing type: inbound always 2-stage (our responsibility), outbound real-time is 1-stage (ACSC direct), outbound RTGS is 2-stage (ACTC→ACSC), outbound SWIFT gpi is multi-stage (ACTC→ACSP→ACSC)

### 2026-02-21 — Exam Integrity Model & Architecture SLA Updates
- **Added:** PayArk exam integrity model — question bank generation (5x pool per exam), randomization engine (weighted retry, answer shuffling, category coverage), anti-cheat measures (encrypted questions, per-question timer, no back-navigation, 48hr cooldown, correct answers never shown), and exam session flow
- **Changed:** Architecture HTML Section 11 — added dev environment testing targets (1K TPS), ISO 20022 message SLA for pacs.008 → pacs.002 flow, removed redundant detailed breakdown section

### 2026-02-21 — Product Named "Payonex"
- **Decided:** Payment House platform product name chosen — **Payonex** (Pay + One + Nexus — unified payment platform)
- **Changed:** README hero title updated to Payonex
- **Changed:** Design Brief updated with product name
- **Added:** Development Plan — populated tech stack from Design Brief decisions, added hardware & infrastructure requirements section covering laptop recommendations (ThinkPad P16, Legion Pro 5, ProArt Studiobook, MacBook Pro), minimum specs (64 GB RAM, 16+ cores, 2 TB NVMe), and Chennai power protection strategy

### 2026-02-21 — Training App Renamed to PayArk
- **Changed:** Training app renamed from "PayForge" to **PayArk** (Academy)
- **Changed:** All certificate prefixes updated — VCPF/VCPE/VCPSA/VCPA → PAKF/PAKE/PAKSA/PAKA (PayArk Certified)
- **Changed:** UI wireframes updated with PayArk branding
- **Changed:** App description updated — "The ark that carries all payment knowledge"

### 2026-02-21 — Training Program Audience & Philosophy Updated
- **Changed:** "Who Is This For?" split into separate architect, developer, and business analyst audience points with level-specific guidance
- **Changed:** "One concept, one module" learning principle now references SRP (Single Responsibility Principle) as its design inspiration
- **Added:** Content Integration Strategy — documents how each video source (YouTube, Udemy, Confluent, etc.) integrates into the app (embeddable vs link-out) with tracking implications
- **Added:** AI Video Generation section — evaluated Synthesia, HeyGen, Pictory, InVideo AI for creating training content from scripts
- **Changed:** Recommended Approach now defines clear roles — Claude Code produces content, builder reviews/studies/generates AI videos, screen recordings deferred to Level 4
- **Changed:** Content Creation Workflow rewritten with role-per-step breakdown, revised time estimates (~1.5 hrs builder effort per module vs previous 4 hrs)
- **Changed:** Level 4 Capstone evaluation redesigned — 3-layer assessment (automated gates + AI code review + written architecture document) replaces vague "working demo + code review + architecture walkthrough"

### 2026-02-08 — Training App Renamed to PayForge

- **Changed:** Training app renamed from "Viceral Academy" to **PayForge**
- **Changed:** All certificates updated (VCPF/VCPE/VCPSA/VCPA now PayForge Certified)
- **Changed:** UI wireframes updated with PayForge branding

### 2026-02-08 — Training Program Plan (PayForge)

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
