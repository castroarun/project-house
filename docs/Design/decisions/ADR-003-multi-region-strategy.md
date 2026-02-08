# ADR-003: Configuration-Driven Multi-Region Strategy
**Status:** Accepted
**Date:** 2026-02-08

## Context
Platform operates across 4 regions (Singapore, Hong Kong, UK, India) with different clearing houses, regulatory requirements, sanctions lists, and operating hours. Need to deploy and maintain code efficiently across all regions.

## Decision
- **Single Docker image** for all regions — no region-specific builds
- **Configuration-driven adapters** — Spring Profiles + Consul/etcd for hot-reload
- **Zero region-conditional code** — No `if (region == "India")` blocks anywhere
- **Atomic pipeline** — All 4 staging regions must pass before any production deployment
- **Clearing adapter pattern** — Pluggable `ClearingAdapter` interface, adapters discovered at runtime

## Alternatives Considered
- **Region-specific builds** — Simpler per-region but creates 4 codebases to maintain; drift is inevitable
- **Feature flags for regions** — Considered but adapters are cleaner; flags used only for incident response (LaunchDarkly)
- **Monorepo with region modules** — Would work but single image is simpler for Kubernetes

## Consequences
- One codebase, one image, one pipeline — dramatically simpler CI/CD
- New country deployment = implement adapter + add config — zero core pipeline changes
- All regions get every code change — no regional drift
- Hotfix protocol needed for emergency region-specific fixes (48h convergence deadline)
- Config Service (Consul/etcd) becomes critical infrastructure — must be highly available
