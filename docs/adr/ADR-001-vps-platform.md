# ADR-001 – VPS Platform Selection

## Status

Accepted

## Date

2026-07-02

## Context

Open Automation Lab requires a permanent environment for research, development, testing and hosting automation services.

The platform must meet the following requirements:

- low annual operating cost,
- full administrative (root) access,
- Docker compatibility,
- 24/7 availability,
- ability to upgrade resources without service migration,
- suitable for long-term experimentation rather than high availability.

Several VPS providers were considered before selecting the initial hosting platform.

## Decision

The project will initially use the **Mikrus VPS 2.1** plan as the hosting platform.

The selected platform provides sufficient resources for the first phases of the project while keeping operational costs extremely low.

The decision is intentionally focused on learning, experimentation and architecture validation rather than production-scale workloads.

## Decision Drivers

The decision was primarily influenced by the following factors:

- very low annual cost,
- full Linux administration capabilities,
- Docker support,
- easy upgrade path,
- active Polish community,
- good fit for personal R&D projects.

## Alternatives Considered

### Hetzner Cloud

**Rejected**

Excellent infrastructure and scalability, but significantly higher operational cost than required for the initial project phase.

### OVH Cloud

**Rejected**

Reliable platform, but provides no significant advantage for a small personal automation laboratory.

### Oracle Cloud Free Tier

**Rejected**

Although attractive from a cost perspective, resource availability is unpredictable and long-term service continuity cannot be guaranteed.

## Consequences

### Advantages

- extremely low operational cost,
- fast project start,
- suitable environment for experimentation,
- sufficient resources for initial Docker-based services,
- upgrade path without redesigning the architecture.

### Disadvantages

- limited RAM,
- limited disk capacity,
- not intended for high availability,
- future project growth may require migration to a larger VPS plan.

## Related Documents

- ADR-000 – Project Principles
- PROJECT.md
- RB-001 – SSH Configuration

## Review

This decision should be reviewed after deploying the initial platform components, including Docker, reverse proxy and n8n.

The platform should be upgraded if one or more of the following conditions become true:

- sustained memory usage exceeds approximately 75%,
- available disk space becomes insufficient,
- CPU becomes a recurring bottleneck,
- additional services cannot be deployed without resource constraints.