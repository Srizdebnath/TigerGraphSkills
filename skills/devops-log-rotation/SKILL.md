---
name: devops-log-rotation
description: >
  Configure and prune TigerGraph log directories. Use when managing server disk space and preventing disk full crashes.
license: MIT
---
# Log Management and Rotation

## When to use this
Use when self-managed TigerGraph servers consume excessive disk space due to query, REST, and loading logs.

## Prerequisites
Access to server filesystem. Links:
- [TigerGraph gadmin Reference](https://docs.tigergraph.com)

## Steps
1. View current log directory allocations (typically located at `~/.tigergraph/log`).
2. Configure log retention rules and sizes using `gadmin`:
   ```bash
   gadmin config set System.LogRetentionDays 7
   gadmin config set System.MaxLogSizeMB 100
   ```
3. Apply changes:
   ```bash
   gadmin config apply -y
   ```
4. Deploy system `logrotate` scripts to compress older logs.

## Common mistakes
- Deleting active log files manually using `rm -rf`, which can cause system log writer descriptors to hang. Use config pruning or copy/null commands.
- Ignoring REST++ log growths, which grow rapidly under high concurrent API traffic.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
