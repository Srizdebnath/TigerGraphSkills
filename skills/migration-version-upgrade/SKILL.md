---
name: migration-version-upgrade
description: >
  Perform version upgrades on self-managed TigerGraph instances. Use when upgrading minor or major database engine releases.
license: MIT
---
# Upgrading TigerGraph Versions

## When to use this
Use when upgrading your self-managed TigerGraph instance (e.g. from version 3.9 to 4.x) to obtain new features and bug fixes.

## Prerequisites
Full database backup snapshot, admin terminal access. Links:
- [TigerGraph Installation Guide](https://docs.tigergraph.com)

## Steps
1. Run a full backup of the database and save the snapshot to a safe remote location:
   ```bash
   gadmin backup save upgrade_backup
   ```
2. Download the target TigerGraph installation tarball package.
3. Stop all database services safely:
   ```bash
   gadmin stop -y
   ```
4. Execute the installation script using the upgrade flag:
   ```bash
   sudo ./install.sh -u
   ```

## Common mistakes
- Upgrading databases without performing a full verified backup snapshot beforehand.
- Trying to run upgrades when database partition services are degraded or down.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
