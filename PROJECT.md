# Open Automation Lab

## Project Vision

Open Automation Lab is a long-term engineering project focused on building a portable, secure and well-documented automation platform.

The project combines infrastructure engineering, containerization, automation, AI workflows and operational best practices into a reproducible reference implementation.

---

# Current Status

## Current Phase

**Phase 02 – Container Platform**

## Current Sprint

**Sprint 3 – Platform Filesystem**

## Overall Progress

| Phase | Status |
|--------|:------:|
| Phase 00 – Foundation | ✅ Completed |
| Phase 01 – Identity & Security | ✅ Completed |
| Phase 02 – Container Platform | 🚧 In Progress |

---

# Current Objectives

- Complete Docker platform provisioning
- Define the platform filesystem layout
- Prepare the first service deployment
- Establish platform documentation standards

---

# Current Risks

| Risk | Status |
|------|--------|
| Direct root login still enabled | Planned for SSH Hardening |
| Password authentication still enabled | Planned for SSH Hardening |

---

# Architecture Decisions

| ADR | Title | Status |
|-----|-------|:------:|
| ADR-000 | Engineering Principles Adoption | ✅ |
| ADR-001 | VPS Platform Selection | ✅ |
| ADR-002 | SSH Key Strategy | ✅ |
| ADR-003 | Container Runtime | ✅ |
| ADR-004 | Platform Filesystem Layout | ✅ |

---

# Platform Summary

| Component | Status |
|-----------|:------:|
| Ubuntu 24.04 LTS | ✅ |
| SSH Key Authentication | ✅ |
| Dedicated Administrator Account | ✅ |
| Docker Engine | ✅ |
| Docker Compose Plugin | ✅ |
| Platform Filesystem Layout | ✅ |
| Reverse Proxy | ⏳ |
| First Service | ⏳ |

---

# Documentation

```
docs/
├── adr/
├── architecture/
├── inventory/
├── journal/
├── knowledge/
├── principles/
├── runbooks/
└── templates/
```

---

# Engineering Principles

The project follows the engineering principles defined in:

**ADR-000 – Engineering Principles Adoption**

---

# Next Milestones

1. Finalize ADR-004 – Platform Filesystem Layout
2. Create the platform directory structure (`/opt/oal`)
3. Deploy the first Docker stack
4. Configure Caddy as the reverse proxy
5. Enable HTTPS
6. Deploy the first production service
7. Complete SSH Hardening

---

# Long-Term Roadmap

- Automation Platform
- AI Workflows
- Home Automation
- Monitoring & Observability
- Backup & Disaster Recovery
- CI/CD
- Infrastructure as Code

---

# Last Updated


# Releases

| Version| Status  | Description |
|--------|:------: |-------------|
| v0.1.0 | Planned | Foundation completed |
| v0.2.0 | Planned | Reference Platform |
| v0.3.0 | Planned | Core Services |
| v1.0.0 | Future  | Production-ready automation platform |