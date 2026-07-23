---
name: security-audit-logging
description: >
  Enable, configure, and inspect TigerGraph database audit logs. Use when tracing user commands, schema edits, and login events.
license: MIT
---
# Enabling & Reading Audit Logs

## When to use this
Use when compliance requirements mandate auditing of database logins, schema modifications, and data access queries.

## Prerequisites
Admin access to database server logs. Links:
- [TigerGraph Security Documentation](https://docs.tigergraph.com)

## Steps
1. Enable auditing inside config settings:
   ```bash
   gadmin config set System.AuditLog.Enable true
   gadmin config apply -y
   gadmin restart -y
   ```
2. Locate audit log files on the host (typically under `~/.tigergraph/log/audit.log`).
3. Analyze log lines, which contain timestamps, client IPs, user accounts, and executed GSQL statements.

## Common mistakes
- Assuming audit logs are enabled by default on self-managed clusters. They must be explicitly enabled and config applied.
- Not configuring log rotation, which can lead to disk space exhaustion on high-traffic databases.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
