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

## Step 1 – Verify the platform root directory

```bash
ls -ld /opt/oal
```

If the directory does not exist, continue with the next step.

---

## Step 2 – Create the platform root directory

```bash
sudo mkdir -p /opt/oal
```

---

## Step 3 – Create the standard directory layout

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

## Step 4 – Set ownership

Platform directories are owned by the operating system.

```bash
sudo chown -R root:root /opt/oal
```

---

## Step 5 – Configure permissions

```bash
sudo chmod -R 755 /opt/oal
```

---

## Step 6 – Verify the directory structure

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

## Step 7 – Verify ownership

```bash
ls -ld /opt/oal /opt/oal/*
```

Expected owner:

```text
root root
```

---

# Verification

Verify that:

- the platform root directory exists,
- all standard directories have been created,
- ownership is set to `root:root`,
- permissions are set to `755`,
- the directory structure matches ADR-004.

---

# Rollback

Remove the platform directory.

```bash
sudo rm -rf /opt/oal
```

Rollback is only permitted before any production services have been deployed.

---

# Troubleshooting

## `tree` command not found

Install the package:

```bash
sudo apt install tree
```

---

## Permission denied

Verify that the current user has administrative privileges.

```bash
id
```

Verify:

```bash
groups
```

The administrator account should belong to the `sudo` group.

---

# Automation

Reserved.

Future implementation:

```text
automation/bash/RB-004-platform-filesystem-layout.sh
```

---

# Lessons Learned

The platform filesystem should be established before deploying the first service.

A consistent directory layout simplifies deployment, maintenance, backup and disaster recovery.

---

# Completion Criteria

The runbook is considered complete when:

- `/opt/oal` exists,
- all standard directories have been created,
- ownership is `root:root`,
- permissions are correctly configured,
- the directory structure complies with ADR-004.

---

# Idempotency

This procedure is idempotent.

Running the runbook multiple times does not modify an already compliant platform.