# ADR-001 - VPS Platform Selection

## Status

Accepted

## Date

2026-07-02

## Context

Open Automation Lab requires a permanent environment for research, development, testing and hosting automation services.

The hosting platform must provide:

- low operating cost,
- full administrative access,
- Docker compatibility,
- continuous availability,
- resource scalability,
- suitability for long-term experimentation.

## Decision

The project uses the Mikrus VPS 2.1 plan as the initial hosting platform.

## Decision Drivers

- Very low annual cost
- Full Linux administration capabilities
- Docker compatibility
- Easy upgrade path
- Active community
- Excellent fit for personal R&D

## Alternatives Considered

### Hetzner Cloud

Rejected.

Provides excellent infrastructure but exceeds the project's initial requirements and budget.

### OVH Cloud

Rejected.

Reliable platform with no significant advantage for the current project scope.

### Oracle Cloud Free Tier

Rejected.

Long-term resource availability cannot be guaranteed.

## Consequences

### Advantages

- Low operational cost
- Rapid project start
- Docker-ready environment
- Upgrade path without redesign
- Suitable for experimentation

### Disadvantages

- Limited RAM
- Limited storage
- Not designed for production workloads
- Future growth may require migration

## Related Documents

- ADR-000 – Engineering Principles Adoption
- ADR-003 – Container Runtime
- PROJECT.md

## Review

Review this decision whenever platform requirements exceed the capabilities of the selected VPS plan.