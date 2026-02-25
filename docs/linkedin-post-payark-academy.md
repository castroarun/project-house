# LinkedIn Post 2 — PayArk Academy (Draft Final)

**Date:** 2026-02-21
**Angle:** Builder journey — learning infrastructure
**CTA:** Collaborators, co-learners, co-curators
**Visuals:** Carousel — (1) PayArk dashboard wireframe or Module 1 screenshot, (2) Certification path diagram (PAKF→PAKE→PAKSA→PAKA)
**Timing:** Post 3-5 days after Post 1 (PayoneX Architecture)

---

Last week I shared PayoneX — the enterprise payment platform I'm designing
across 4 countries, 5 clearing networks, and a 6-tier Kafka pipeline.

The response was clear: how do you actually learn all of this?

So I built the answer. PayArk — a structured, self-paced training academy
that takes you from zero to payment architect.

44 modules. 4 certification levels. 32 weeks.

→ Level 1: Payment Foundations (PAKF) — 12 modules, 6 weeks
   Payment lifecycles, ISO 20022, clearing houses, compliance workflows,
   Java 21, SOLID, hexagonal architecture, DDD

→ Level 2: Platform Engineer (PAKE) — 16 modules, 8 weeks
   Kafka deep dive, Spring Boot, PostgreSQL+Citus, Redis, ClickHouse,
   event sourcing, saga patterns, circuit breakers, testing strategies

→ Level 3: Payment Systems Architect (PAKSA) — 16 modules, 10 weeks
   Docker, Kubernetes, Istio, Vault, Prometheus, OpenTelemetry,
   multi-region deployment, security architecture, CI/CD, performance engineering

→ Level 4: Capstone — Build Payment House (PAKA) — 8 weeks
   Build a working subset of PayoneX end-to-end. No theory. Ship code.

Every module maps directly to a PayoneX component.
This isn't a generic curriculum — it's an architecture-driven learning path.

Who is this for?
→ Developers — Levels 1-2 cover domain knowledge + implementation patterns
→ Architects — Levels 3-4 cover multi-region, security, infrastructure, system design
→ Business Analysts — Level 1 (M01-M04) covers payment flows, ISO 20022,
   clearing houses, and compliance — no code required

Now here's where it gets serious — the exam system.

I'm not building a checkbox certification.
The question bank is 5x the exam size — 300 questions for a 60-question exam.
Questions stored encrypted in the database. Answer keys computed at grading time, not stored.

Every attempt is unique:
→ Random question selection from the pool — never the same set twice
→ Answer positions shuffled every attempt
→ Per-question timer (60-90s MCQ, 5 min scenario)
→ No back-navigation during exams
→ 48-hour cooldown between reattempts
→ Correct answers are never shown — only category weakness breakdowns
→ Questions you got wrong have a higher chance of reappearing

And for Level 3, it's not just MCQs —
you write a full system design document that gets evaluated against an architecture rubric.

Level 4 is the real test: build PayoneX.
Automated gates (tests, coverage, lint) + AI code review + written architecture walkthrough.
You can't fake a working codebase.

Content sourcing — leveraging the best, not reinventing:
→ Confluent Developer for Kafka (free, official, excellent)
→ Spring Academy for Spring Boot (official)
→ Redis University for caching patterns (free)
→ Curated YouTube — handpicked best explainers per topic
→ Udemy + Baeldung where depth demands paid content

The academy itself is open.
Module 1 is live. The curriculum is public.

If you work in payments, fintech, or core banking —
or you're a developer who wants to genuinely master international payment systems —

I'm looking for co-learners and co-curators.
Learn alongside, suggest better resources, challenge the questions, improve the curriculum.
Let's build this knowledge base together.

→ PayArk Academy: https://castroarun.github.io/project-house/Design/payark-academy-portal.html
→ Full curriculum: https://castroarun.github.io/project-house/Design/payark-academy-portal.html#curriculum
→ PayoneX platform: https://castroarun.github.io/project-house/Design/payonex.html
→ PayoneX architecture: https://castroarun.github.io/project-house/Design/payment-architecture.html
→ GitHub: https://github.com/castroarun/project-house

Built using my 9-step development process:
https://www.linkedin.com/pulse/clarity-clutter-why-ai-assisted-development-needs-arun-castromin-hmxzc/

#PayArk #PayoneX #Payments #Fintech #LearningInPublic #BuildInPublic #Kafka #ISO20022 #PaymentArchitecture #SystemDesign #CoreBanking

---

## Visual Recommendations

1. **Image 1:** Screenshot of PayArk Academy portal hero — certificate mock, metrics bar, "Master the PayoneX platform" tagline (`payark-academy-portal.html`)
2. **Image 2:** Screenshot of the 4-level certification path section or the full curriculum table (`payark-academy-portal.html#levels` or `#curriculum`)

## Live Pages

| Page | URL |
|------|-----|
| PayArk Academy | https://castroarun.github.io/project-house/Design/payark-academy-portal.html |
| PayoneX Platform | https://castroarun.github.io/project-house/Design/payonex.html |
| Architecture | https://castroarun.github.io/project-house/Design/payment-architecture.html |
| Hub | https://castroarun.github.io/project-house/ |

## Post Checklist

- [x] Single-line intro branching from PayoneX (Post 1)
- [x] Module structure (44 modules, 4 levels, 32 weeks)
- [x] Certification stages with abbreviations (PAKF→PAKE→PAKSA→PAKA)
- [x] Roles addressed (Developer, Architect, BA)
- [x] Exam integrity deep dive (encryption, randomization, anti-cheat)
- [x] Assessment beyond MCQ (system design document, architecture walkthrough, automated gates)
- [x] Content sourcing strategy (free + paid)
- [x] CTA: co-learners + co-curators
- [x] PayArk Academy live link
- [x] 9-step process article link
- [x] Hashtags
