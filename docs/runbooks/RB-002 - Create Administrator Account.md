# RB-002 - Create Administrator Account

## Purpose

Create a dedicated administrator account for managing the Open Automation Lab platform.

Direct day-to-day administration should not be performed using the `root` account.

---

## Scope

This runbook applies to every Open Automation Lab host.

---

## Prerequisites

- Ubuntu 24.04 LTS
- Root access
- SSH connectivity
- ADR-002 accepted

---

## Related Documents

- ADR-002 – SSH Key Strategy
- HOST.md
- PB-001 – Provision Reference Platform

---

# Manual Procedure

## Step 1 – Create the administrator account

```bash
sudo adduser piotr
```

---

## Step 2 – Add the user to the sudo group

```bash
sudo usermod -aG sudo piotr
```

---

## Step 3 – Create the SSH directory

```bash
sudo mkdir -p /home/piotr/.ssh
```

---

## Step 4 – Copy the authorized keys

```bash
sudo cp /root/.ssh/authorized_keys /home/piotr/.ssh/
```

---

## Step 5 – Configure ownership

```bash
sudo chown -R piotr:piotr /home/piotr/.ssh
```

---

## Step 6 – Configure permissions

```bash
sudo chmod 700 /home/piotr/.ssh
sudo chmod 600 /home/piotr/.ssh/authorized_keys
```

---

## Step 7 – Verify SSH login

Connect using:

```bash
ssh oal
```

---

## Step 8 – Verify administrative privileges

```bash
sudo whoami
```

Expected output:

```text
root
```

---

# Verification

Verify:

- administrator account exists
- SSH login works
- passwordless authentication works
- sudo privileges work

---

# Rollback

```bash
sudo deluser --remove-home piotr
```

Rollback is only permitted before the account becomes the primary administrator.

---

# Troubleshooting

## Permission denied

Verify ownership and permissions of:

```text
~/.ssh
authorized_keys
```

---

# Automation

Reserved.

Future implementation:

```
automation/bash/RB-002-create-administrator-account.sh
```

---

# Lessons Learned

Administrator accounts should be verified before disabling root access.

---

# Completion Criteria

- Administrator account created
- SSH login verified
- sudo verified

---

# Idempotency

Partially idempotent.

Existing users should be verified before re-running the procedure.