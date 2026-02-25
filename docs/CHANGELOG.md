# Payment House - Changelog

All notable changes to this project are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/).

---

## [Unreleased]

### 2026-02-25 — Branding Polish: Rename, Favicons, LinkedIn Links
- **Changed:** Renamed `payonex-portal.html` → `payonex.html` (cleaner brand URL)
- **Added:** Browser tab favicons (inline SVG) to all pages:
  - PX (blue) for PayoneX pages, PA (gold) for PayArk, PH (cyan) for hub
- **Changed:** LinkedIn posts updated with correct live GitHub Pages URLs
  - Post 1 (Architecture): added PayoneX platform link
  - Post 2 (Academy): replaced placeholder with live PayArk Academy link, added all page URLs
- **Changed:** All cross-references updated (hub, PayArk portal, changelog)

### 2026-02-25 — Isometric Background Pattern + GitHub Pages Deployment
- **Changed:** Replaced feTurbulence noise texture with isometric diamond SVG pattern on PayArk Academy portal
  - Clean geometric tessellation at 0.05 opacity, subtle cyan/violet radial overlays
- **Added:** `docs/Design/bg-pattern-sampler.html` — 10 background pattern options (Dot Grid, Grid Lines, Crosshatch, Honeycomb, Circuit Board, Topographic, Isometric, Noise Grain, Radial Pulse, Plus Signs)
- **Changed:** Reverted navy blue background experiment back to original near-black palette (`#06070b` base)
- **Added:** `docs/index.html` — Hub page linking to all three showcase pages
- **Added:** GitHub Pages deployment serving from `docs/` folder
  - PayoneX Architecture, PayoneX Portal, PayArk Academy Portal now live

### 2026-02-25 — PayArk Academy Portal: Navy Theme, Collapsible Curriculum, White Certificate
- **Changed:** Background palette switched from near-black to deep navy blue (inspired by Conexus design)
  - `--bg: #080a1a`, `--bg2: #0d1030`, `--bg3: #0f1338`, `--bg4: #141845`
  - Atmosphere gradient: `linear-gradient(170deg, #080a1a → #0d1030 → #111545 → #0a0e28)`
  - Borders: `#1e2460` / `#2a3070` (indigo-tinted instead of grey)
- **Changed:** Certificate mock redesigned with white/cream background like a real certificate
  - Background: `#fffef8 → #fdf8ed` gradient, gold border `rgba(180,150,80,.35)`
  - Text colors: dark navy `#1a1a2e` for headings, `#8b6914` gold for cert name, `#4b5563` for details
- **Added:** Collapsible curriculum levels — click level header to expand/collapse module table
  - PAKF opens by default, PAKE/PAKSA/PAKA collapsed
  - Smooth CSS grid-template-rows animation, rotating arrow indicator
- **Changed:** Explore section simplified from card links to inline text mention with link to architecture page
- **Removed:** PayoneX Platform card and Architecture Deep Dive card from Explore section

### 2026-02-25 — PayArk Academy Portal: Curriculum Section + Explore Cleanup
- **Added:** Full 44-module course curriculum section (Section 02) after "Not Another Tutorial Playlist"
  - Level 1 PAKF: 12 modules (M01–M12) — Payment Foundations, 6 weeks
  - Level 2 PAKE: 16 modules (M13–M28) — Platform Engineer, 8 weeks
  - Level 3 PAKSA: 16 modules (M29–M44) — Systems Architect, 10 weeks
  - Level 4 PAKA: 4 capstone sprints (S1–S4) — Build Payment House, 8 weeks
- **Added:** Summary stats bar (44 modules, 4 certs, 32 weeks, ~200 hrs, 50 q/module)
- **Added:** Curriculum nav tab in pill navigation
- **Added:** Architecture Deep Dive link in Explore section
- **Changed:** Section numbering adjusted (02→03→04→05→06→07) to accommodate new Curriculum section
- **Removed:** Skill Tree Visualization link from Explore section
- **Removed:** PayArk Academy App link from Explore section (led to GitHub)
- **Changed:** Mobile responsive styles for curriculum tables (hide topics column on small screens)

### 2026-02-25 — PayArk Academy Portal (Landing Page)
- **Added:** `docs/Design/payark-academy-portal.html` — Premium landing page for PayArk Academy, matching PayoneX portal design system
- **Added:** Gold-bordered PAKA certificate mock in hero section with 3D tilt perspective, gold shimmer animation, seal, and credential layout
- **Added:** Self-certification messaging — "The builder who wrote the quiz engine can't guarantee a pass"
- **Added:** 4-level certification path badges (PAKF → PAKE → PAKSA → PAKA) in hero
- **Added:** Exam Integrity section — 6 anti-cheat cards (5× pool ratio, answer shuffle, forward-only, answers never shown, 48hr cooldown, encrypted at rest)
- **Added:** Content Sourcing section with animated bar charts — 80% YouTube curated, 15% AI-generated, 5% MDX reading/labs
- **Added:** Sourcing philosophy panel explaining curation vs creation strategy
- **Added:** 6 USP comparison cards with "Others vs PayArk" format (Real Codebase, Domain+Engineering, Cheat-Proof, Micro-Modules, 4-Level Progression, Free & Open)
- **Added:** 4-level certification track as horizontal scroll-snap cards with module lists and exam requirements
- **Added:** Explore section linking to live app, skill tree, and PayoneX architecture portal
- **Added:** Same premium design system: scroll-reveal animations, glassmorphism cards, atmospheric background, frosted nav, animated counters

### 2026-02-25 — PayoneX Portal Branding Fix
- **Changed:** `docs/Design/payonex.html` — Hero h1 now matches `payment-architecture.html` branding exactly (gradient text white→blue→cyan, underline bar, glowing cyan dot with pulse animation)
- **Changed:** Hero stat "12 Clearing Houses" → "5 Clearing Rails" (honest count: RTGS, Real-Time, Batch, Cross-Border, UPI)

### 2026-02-25 — PayoneX Architecture Portal (Premium Rebuild)
- **Changed:** `docs/Design/payonex.html` — Complete premium rebuild of the front-door landing page for LinkedIn sharing
- **Added:** Scroll-reveal animations (IntersectionObserver fade-in/slide-up with stagger delays) across all sections
- **Added:** Glassmorphism card design with frosted glass backdrop-filter, subtle inner gradients, and hover lift effects
- **Added:** Animated number counters on hero stats (count-up on scroll into view)
- **Added:** Atmospheric background with layered radial gradients and masked dot grid overlay
- **Added:** Frosted glass sticky navigation with scroll shadow, brand wordmark, and IntersectionObserver active state tracking
- **Added:** Animated Kafka event bus bar with flowing gradient lines and topic pipeline
- **Added:** 5-phase build roadmap as horizontal scroll-snap cards with phase-colored accents and deliverable lists
- **Added:** ADR decision cards with question/chose/rationale format
- **Added:** 4 PayoneX vocabulary cards (Phantom, ACL, Config-Driven Region, Accounting Saga) with colored left-border accents
- **Added:** 9 engineering patterns in a clean table with colored dots per pattern
- **Added:** Infrastructure specs table + power protection strategy cards
- **Added:** Explore section with 4 linked cards (Architecture, Metro Map, Skill Tree, Academy) with hover arrows and tags
- **Added:** Animated Kafka event bus bar showing full topic pipeline across all 6 tiers
- **Added:** 5-phase build roadmap with deliverables (Phase 0 Done, Phase 1 Next, Phases 2-4 Planned)
- **Added:** 4 PayoneX vocabulary concepts: Phantom, ACL, Config-Driven Region, Accounting Saga
- **Added:** 9 engineering patterns table (Hexagonal, Event Sourcing, DDD, Saga, Strategy, ACL, Circuit Breaker, Outbox, SOLID+CUPID)
- **Added:** Development infrastructure specs with power protection strategy for Chennai-based dev
- **Added:** Explore section linking to Architecture, Metro Map, Skill Tree, and PayArk Academy

### 2026-02-25 — Project Status & README Updated with Live Links
- **Changed:** PROJECT-STATUS.md v2.0 — full inventory of everything done (25 items), live GitHub Pages links for all 12 HTML pages, related repos section, ADR-004 added
- **Changed:** README — LAUNCHPAD stage updated from `idea` to `building` (25% progress), added "Live Design Pages" section with 7 key HTML links, updated project structure tree (all HTML files + ADRs + LinkedIn posts), roadmap updated with 5 new completed items
- **Added:** GitHub Pages links consolidated — 7 PayoneX design pages + 4 PayArk skill tree variants

### 2026-02-24 — PayArk Academy App Built (Module 1 MVP)
- **Added:** New repo `payark-academy` — full Next.js 16 app with TypeScript, Tailwind v4, Supabase auth
- **Added:** Complete app shell with 7 routes: dashboard, login, curriculum, module overview, content step, quiz
- **Added:** 44-module curriculum metadata with 4 certification levels (PAKF, PAKE, PAKSA, PAKA)
- **Added:** Module 1 ("How Payments Work") fully built: 3 video steps, 2 MDX reading articles, 1 lab, 1 quiz
- **Added:** 3 MDX articles (~1000 words each): Payment Lifecycle, Clearing vs Settlement, Correspondent Banking
- **Added:** 50-question quiz bank with difficulty spread (30% easy, 50% medium, 20% hard)
- **Added:** Quiz engine: Fisher-Yates shuffle, per-question timer, forward-only navigation, 70% pass mark
- **Added:** 14 React components: UI primitives, dashboard cards, module views, quiz engine
- **Added:** Supabase schema with RLS policies (profiles, module_progress, content_progress, quiz_attempts)
- **Added:** Dark fintech theme matching PayoneX design tokens
- **Added:** Build verified — `next build` compiles cleanly with all 7 routes

### 2026-02-21 — PayArk Skill Tree Hybrid Visualization
- **Added:** `docs/Design/payark-skilltree-hybrid.html` — Standalone showpiece HTML visualization of the PayArk Training Academy curriculum
- **Added:** Hybrid approach: CSS Grid layout for module cards + D3.js SVG overlay for connection lines + GSAP ScrollTrigger for scroll-driven animations
- **Added:** All 44 modules (M01-M44) and 4 capstone sprints (S1-S4) rendered as interactive cards across 4 color-coded levels (Blue/Cyan/Violet/Amber)
- **Added:** Exam gate bars between levels showing certification requirements (PAKF/PAKE/PAKSA/PAKA)
- **Added:** PAKA certification badge section with gold glow animation
- **Added:** Exam Integrity Model section — question bank visual, randomization engine cards, anti-cheat layer stack animation, exam session flow steps
- **Added:** Content Pipeline section — 10 source cards, integration strategy, 5-step production pipeline
- **Added:** Click-to-open detail panel (slides from right) showing full module info: topics, hands-on project, PayoneX component mapping
- **Added:** D3.js draws SVG bezier connection lines between sequential module cards within each level
- **Added:** GSAP ScrollTrigger animations: hero fade-in, card stagger, exam gate scale-in, badge bounce, layer stack slide-in, source card fan-out, connection line draw
- **Added:** Matches PayoneX design system (dark theme, Outfit + JetBrains Mono fonts, all color tokens)

### 2026-02-21 — LinkedIn Post 2: PayArk Academy Draft
- **Added:** `docs/linkedin-post-payark-academy.md` — LinkedIn post draft focused on PayArk training academy (44 modules, 4 certifications, exam integrity, sourcing strategy, CTA for co-learners)

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
