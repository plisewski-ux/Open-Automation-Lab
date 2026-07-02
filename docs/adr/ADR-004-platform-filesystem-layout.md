# RB-004 - Platform Filesystem Layout

## Purpose

Create the standard Open Automation Lab platform directory structure as defined in ADR-004.

The procedure establishes the platform root directory and prepares the host for future service deployments.

---

## Scope

This runbook applies to every Open Automation Lab host.

---

## Prerequisites

- Ubuntu 24.04 LTS
- Docker Engine installed
- Administrator account with sudo privileges
- ADR-004 accepted

---

## Related Documents

- ADR-004 – Platform Filesystem Layout
- HOST.md
- PB-001 – Provision Reference Platform

---

# Manual Procedure

## Step 1 – Create the platform root directory

```bash
sudo mkdir -p /opt/oal
```

---

## Step 2 – Create the standard directory layout

```bash
sudo mkdir -p \
    /opt/oal/stacks \
    /opt/oal/data \
    /opt/oal/config \
    /opt/oal/backups \
    /opt/oal/scripts \
    /opt/oal/shared
```

---

## Step 3 – Set ownership

The platform directories are managed by administrators.

```bash
sudo chown -R root:docker /opt/oal
```

---

## Step 4 – Configure permissions

```bash
sudo chmod -R 775 /opt/oal
```

---

## Step 5 – Verify the directory structure

```bash
tree /opt/oal
```

Expected output:

```text
/opt/oal
├── backups
├── config
├── data
├── scripts
├── shared
└── stacks
```

---

## Step 6 – Verify ownership

```bash
ls -ld /opt/oal/*
```

Expected owner:

```text
root docker
```

---

# Verification

Verify:

- platform root exists
- all standard directories exist
- ownership is correct
- permissions are correct

---

# Rollback

Remove the platform directory.

```bash
sudo rm -rf /opt/oal
```

Rollback is only permitted before any production services have been deployed.

---

# Troubleshooting

## tree command not found

Install:

```bash
sudo apt install tree
```

---

## Permission denied

Verify the current user belongs to the `docker` group.

```bash
id
```

Reconnect the SSH session if necessary.

---

# Automation

Reserved.

Future implementation:

```
automation/bash/RB-004-platform-filesystem-layout.sh
```

---

# Lessons Learned

The platform filesystem should be established before deploying the first service.

This ensures that every service follows the same directory structure and backup strategy.

---

# Completion Criteria

The runbook is considered complete when:

- `/opt/oal` exists
- all standard directories have been created
- ownership is correct
- permissions are verified
- directory structure matches ADR-004

# Idempotency

The procedure is idempotent.

Running this runbook multiple times does not modify an already compliant platform.