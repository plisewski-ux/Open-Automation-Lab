# RB-003 - Install Docker Engine

## Purpose

Install Docker Engine from Docker's official APT repository.

---

## Scope

This runbook applies to every Open Automation Lab host.

---

## Prerequisites

- Ubuntu 24.04 LTS
- Internet access
- sudo privileges
- ADR-003 accepted

---

## Related Documents

- ADR-003 – Container Runtime
- ADR-001 – VPS Platform Selection
- PB-001 – Provision Reference Platform

---

# Manual Procedure

## Step 1 – Install prerequisites

```bash
sudo apt update

sudo apt install -y \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

---

## Step 2 – Create the keyring directory

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

---

## Step 3 – Download the Docker GPG key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg \
| sudo gpg --dearmor \
-o /etc/apt/keyrings/docker.gpg
```

```bash
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

---

## Step 4 – Configure the Docker repository

```bash
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" \
| sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

---

## Step 5 – Install Docker

```bash
sudo apt update

sudo apt install -y \
    docker-ce \
    docker-ce-cli \
    containerd.io \
    docker-buildx-plugin \
    docker-compose-plugin
```

---

## Step 6 – Add the administrator to the Docker group

```bash
sudo usermod -aG docker piotr
```

Reconnect the SSH session.

---

## Step 7 – Verify the installation

```bash
docker --version
docker compose version
docker run hello-world
```

---

# Verification

Verify:

- Docker Engine
- Docker Compose
- Buildx
- containerd
- hello-world container

---

# Rollback

```bash
sudo apt remove docker-ce docker-ce-cli containerd.io
```

---

# Troubleshooting

Verify:

```bash
systemctl status docker
systemctl status containerd
```

---

# Automation

Reserved.

Future implementation:

```
automation/bash/RB-003-install-docker-engine.sh
```

---

# Lessons Learned

Always install Docker from the official Docker repository.

---

# Completion Criteria

- Docker installed
- Compose installed
- hello-world executed successfully

---

# Idempotency

Partially idempotent.

The procedure may be re-executed safely, but existing package versions should be reviewed before upgrades.