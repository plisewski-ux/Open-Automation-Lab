# Reference Host

Provider

Mikrus VPS 2.1

Operating System

Ubuntu 24.04 LTS

Architecture

x86_64

Container

LXC

RAM

1 GB

Disk

10 GB

IPv6

Enabled

Purpose

Reference deployment platform for Open Automation Lab.

## Provisioning

Provisioned by:
Manual

Date:
2026-07-02

Reference ADR:
ADR-001

## Lifecycle

Current Status

Active

Last Review

2026-07-02

## Time Synchronization

Time synchronization is provided by the Proxmox host.

`systemd-timesyncd` is intentionally inactive inside the LXC container due to the `ConditionVirtualization=!container` systemd condition.


# Mikrus LXC Notes

## Overview

The reference platform is deployed inside an LXC container hosted by Proxmox.

Some systemd services are expected to remain inactive or failed due to container isolation.

## Expected Behaviour

### systemd-timesyncd

Status:

Inactive

Reason:

Time synchronization is provided by the Proxmox host.

### systemd-remount-fs.service

Status:

Failed

Reason:

LXC containers cannot remount the root filesystem.

### sys-kernel-config.mount

Status:

Failed

Reason:

`configfs` is managed by the host kernel and is not available inside the container.

## Conclusion

These states are expected and do not indicate a problem with the platform.

## Platform Root

Platform Root:

/opt/oal

Standard directories:

- stacks
- data
- config
- backups
- scripts
- shared