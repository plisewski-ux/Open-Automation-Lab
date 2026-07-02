# ADR-003 - Container Runtime

## Status

Accepted

## Date

2026-07-02

## Context

Open Automation Lab requires a stable and well-supported container runtime for hosting automation services.

The platform must support:

- Docker Compose
- long-term maintainability
- official package repositories
- predictable upgrade path
- broad community support

## Decision

The platform uses Docker Engine installed from Docker's official APT repository.

Distribution packages and Snap packages are not used.

## Decision Drivers

- Official vendor support
- Latest stable releases
- Predictable update cycle
- Docker Compose Plugin support
- Broad ecosystem compatibility

## Alternatives Considered

### Ubuntu docker.io package

Rejected.

Usually behind upstream Docker releases.

### Docker Snap package

Rejected.

Introduces unnecessary complexity and differs from standard Linux server deployments.

### Podman

Rejected.

Technically capable, but Docker remains the standard runtime for this project.

## Consequences

### Advantages

- Official support
- Consistent installation
- Latest stable features
- Easier troubleshooting
- Portable deployment documentation

### Disadvantages

- External APT repository
- Additional GPG key management

## Related Documents

- ADR-000 – Engineering Principles Adoption
- ADR-001 – VPS Platform Selection
- Engineering-Principles.md

## Review

Review when major Docker releases introduce architectural changes or when the platform migrates to another container runtime.
