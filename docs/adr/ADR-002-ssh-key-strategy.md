# ADR-002 - SSH Key Strategy

## Status

Accepted

## Date

2026-07-02

## Context

Open Automation Lab will consist of multiple environments requiring secure SSH administration.

A consistent authentication strategy is required to simplify management while maintaining strong security.

## Decision

SSH authentication follows these principles:

- ED25519 is the standard key algorithm.
- Every environment has its own dedicated key pair.
- Private keys are never copied between devices.
- Keys follow a consistent naming convention.
- Administrators use individual user accounts.
- Direct root login will be disabled after the migration to SSH key authentication has been verified.

## Reference

Example key names:

```text
id_ed25519_openautomationlab
id_ed25519_github
id_ed25519_homelab
id_ed25519_router
```

## Decision Drivers

- Strong authentication
- Least privilege
- Credential isolation
- Simplified key rotation
- Easier auditing

## Alternatives Considered

### Shared SSH key across all environments

Rejected.

Compromising a single private key would require replacing credentials across every managed environment.

## Consequences

### Advantages

- Independent credential management
- Improved security
- Easier auditing
- Safer key rotation

### Disadvantages

- More keys to manage
- Documentation must remain accurate

## Related Documents

- ADR-000 – Engineering Principles Adoption
- RB-001 – SSH Configuration

## Review

Review this strategy whenever new environments or administrators are added.