# Payment House - Claude Code Instructions

## Project Info
- **Name:** Payment House
- **Stage:** Conception
- **Tracking:** Klarity Dashboard (no Jira)
- **Tech Stack:** TBD

## Project-Specific Rules
- No Jira integration for this project — use Klarity dashboard
- Tech stack has NOT been finalized — do not assume any framework
- Currently in conception/requirements gathering phase (Step 2 of 9-step workflow)

## Workflow: How This Project Operates

### Agent Roles
| Agent/Session | Purpose | When to Use |
|---|---|---|
| **Desktop Claude** | Ideation, brainstorming, architecture debates | User does this separately |
| **Claude Code (here)** | File management, build, code, git | All implementation work |
| **Plan mode** | Before any multi-file feature | Always before major build steps |

**Desktop is for thinking, Claude Code is for doing.**
User brings discussion dumps here. Claude Code files them and updates project state.

### When User Pastes a Desktop Session Dump

Follow this exact sequence:

1. **Save it** → `docs/brain-dump/NNN-descriptive-name.md` (next sequential number)
2. **Extract decisions** → If any architecture/tech decisions were made, create or update ADR files in `docs/Design/decisions/ADR-NNN-topic.md`
3. **Update design docs** → If the dump contains requirements, update `docs/Design/APP_PRD.md` or create new `docs/Design/*-DESIGN.md` files as needed
4. **Update DESIGN-BRIEF.md** → If high-level vision changed, update `docs/Design/DESIGN-BRIEF.md`
5. **Update PROJECT-STATUS.md** → Reflect any progress
6. **Update CHANGELOG.md** → Add dated entry for everything that changed
7. **Summarize back** → Tell the user what was filed and what decisions were captured

### Changelog — MANDATORY

**File:** `docs/CHANGELOG.md`

Update the changelog on EVERY session that changes project state. This includes:
- Brain dumps filed
- Design docs created or updated
- ADRs added
- Tech stack decisions
- Code written, features built
- Bugs fixed
- Anything removed

**Format per entry:**
```markdown
### YYYY-MM-DD — Short Description
- **Added:** New features, files, capabilities
- **Changed:** Modifications to existing things
- **Decided:** Architecture/tech decisions made (link to ADR)
- **Removed:** Things taken out
- **Fixed:** Bug fixes
```

Never skip this. The changelog is the single source of truth for "what happened and when."

### Design Document Hierarchy (Layered)

Documents evolve from informal → formal. Never skip layers:

```
docs/brain-dump/NNN-*.md        ← Raw ideation (from Desktop dumps)
    ↓ distilled into
docs/Design/DESIGN-BRIEF.md     ← High-level vision (evolving, informal)
    ↓ formalized into
docs/Design/APP_PRD.md          ← Detailed requirements (approved before build)
    ↓ broken into
docs/Design/*-DESIGN.md         ← Specific design docs (architecture, API, data model, flows)
```

### Architecture Decision Records (ADRs)

Every significant technical decision gets an ADR in `docs/Design/decisions/`:

**File format:** `ADR-NNN-kebab-case-topic.md`

**Template:**
```markdown
# ADR-NNN: [Title]
**Status:** Proposed | Accepted | Superseded by ADR-XXX
**Date:** YYYY-MM-DD

## Context
What's the situation? What problem are we solving?

## Decision
What we chose.

## Alternatives Considered
What else we looked at and why we didn't pick it.

## Consequences
What this means going forward — tradeoffs, things to watch.
```

### Phased Build Strategy

This is a large project. Build in phases:
```
Phase 0: Proof of Concept (throwaway, validate core idea)
Phase 1: MVP (smallest working end-to-end)
Phase 2: Core Features (the real product)
Phase 3: Scale & Polish
```

Do NOT start Phase 1 code until PRD is approved.

## Key Docs
- Changelog: `docs/CHANGELOG.md` ← **always update this**
- Brain dumps: `docs/brain-dump/NNN-*.md`
- Design brief: `docs/Design/DESIGN-BRIEF.md`
- PRD: `docs/Design/APP_PRD.md`
- ADRs: `docs/Design/decisions/ADR-NNN-*.md`
- Status: `docs/PROJECT-STATUS.md`
- Dev Clock: `docs/DEV-CLOCK.md`
- Requirements: `inits_n_info/requirements.md`

## File Structure

```
payment-house/
├── .claude/CLAUDE.md              # THIS FILE — project rules
├── README.md                      # Project overview + LAUNCHPAD
├── docs/
│   ├── brain-dump/                # Raw Desktop session dumps
│   │   └── NNN-descriptive-name.md
│   ├── Design/
│   │   ├── DESIGN-BRIEF.md        # High-level vision (evolving)
│   │   ├── APP_PRD.md             # Formal requirements
│   │   ├── ARCHITECTURE-DESIGN.md # System architecture
│   │   ├── API-DESIGN.md          # API contracts
│   │   ├── DATA-MODEL-DESIGN.md   # Database schema
│   │   ├── *-DESIGN.md            # Other domain-specific designs
│   │   └── decisions/
│   │       └── ADR-NNN-*.md       # Architecture Decision Records
│   ├── CHANGELOG.md               # Project changelog (ALWAYS updated)
│   ├── DEV-CLOCK.md               # Time tracking
│   ├── DEVELOPMENT-PLAN.md        # Technical plan
│   ├── PROJECT-STATUS.md          # 9-step workflow
│   ├── GLOSSARY.md                # Domain terms
│   └── TEST-PLAN.csv              # Test matrix
└── inits_n_info/
    └── requirements.md            # Structured requirements
```
