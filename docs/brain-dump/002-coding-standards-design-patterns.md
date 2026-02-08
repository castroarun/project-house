# 002 — Coding Standards & Design Patterns (Desktop Session)

**Date:** 2026-02-08
**Source:** `coding-standards-design-patterns.docx`

## Summary

Coding standards and design patterns for the Enterprise Payment Processing Platform. SOLID + selective CUPID + financial-system-specific disciplines. Java 21, Spring Boot, Hexagonal Architecture.

## Key Decisions

### Design Principles
- **SOLID** — All 5 mandatory. OCP is most critical for multi-region
- **CUPID** — Adopted: Predictability, Domain Alignment. Others subsumed by SOLID
- **Financial Disciplines** — Immutability (Java records), Defensive Calculations (BigDecimal only), Auditability (event sourcing)
- **BigDecimal mandatory** — double/float for money = immediate PR rejection

### Architecture Patterns
1. **Hexagonal (Ports & Adapters)** — Domain at center, zero framework imports in domain/
2. **DDD Bounded Contexts** — 6 contexts: Ingestion, Processing, Compliance, Clearing, Accounting, Reporting
3. **Anti-Corruption Layer** — Per clearing house, isolates external quirks
4. **Event Sourcing** — Immutable events, state derived by replay
5. **Saga (Orchestration)** — 5-step with compensating transactions
6. **Strategy Pattern** — Clearing adapters discoverable at runtime
7. **Template Method** — Processing pipeline skeleton: validate→enrich→screen→clear→book
8. **Specification Pattern** — Composable routing rules
9. **Twelve-Factor App** — Config in env, stateless, port binding, dev/prod parity, logs as streams

### Coding Standards
- Classes (actions): VerbNoun (e.g., ValidateSchema)
- Methods: verbObject() (e.g., submitToClearing())
- Method limit: 20 lines max
- Class limit: 300 lines max
- Nesting: 2 levels max
- Cyclomatic complexity: 10 max
- Comments: WHY not WHAT

### Testing Standards
- Unit: 90% coverage (domain/), AAA pattern, zero Spring context
- Integration: All adapter ports verified
- Contract: Kafka schema tests
- E2E: Per region, pre-deploy staging
- Performance: SLA validation, weekly
- Chaos: Resilience, monthly

### Multi-Region Practices
- Zero if-region-equals blocks — all config-driven (Spring Profiles)
- Single Docker image across all regions
- Atomic deployment pipeline: all 4 staging regions must pass before any prod deploy
- Canary: 5% traffic, 30-min soak

### Changelog & Versioning
- Conventional Commits enforced (commitlint)
- Auto-generated CHANGELOG.md
- Semantic Versioning (MAJOR.MINOR.PATCH)
- ADRs in docs/adr/

### PR Checklist (4-Point Litmus)
1. Domain package touched? → Verify zero framework imports
2. New clearing house requires modifying existing adapters? → OCP violation
3. India config change requires redeploying Singapore? → Fix externalization
4. Can unit test without Kafka/PG/Redis? → If no, DIP broken

## Original File
- `temp_extract/coding-standards-design-patterns.docx`
