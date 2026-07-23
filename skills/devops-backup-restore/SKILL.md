---
name: devops-backup-restore
description: >
  Configure database backups and execute restore operations in TigerGraph. Use when planning disaster recovery pipelines.
license: MIT
---
# Database Backup and Recovery

## When to use this
Use when establishing automatic backup schedules, preparing system upgrades, or restoring data from snapshot backups.

## Prerequisites
Storage space for backups, admin privileges. Links:
- [TigerGraph gadmin Reference](https://docs.tigergraph.com)

## Steps
1. Configure backup directory path:
   ```bash
   gadmin config set System.BackupDirectory /var/backups/tigergraph
   gadmin config apply -y
   ```
2. Create a full backup snapshot of the database:
   ```bash
   gadmin backup save backup_name
   ```
3. Check list of available backups:
   ```bash
   gadmin backup list
   ```
4. Restore the database from a backup (requires stopping services):
   ```bash
   gadmin restore backup_name
   ```

## Common mistakes
- Storing backups on the same disk array as the active database. If the disk array crashes, you lose both database and backups. Route backups to remote mount drives.
- Running restore commands while database services are active, which can corrupt the restore state.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
