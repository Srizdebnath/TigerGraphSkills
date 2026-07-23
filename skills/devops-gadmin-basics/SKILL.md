---
name: devops-gadmin-basics
description: >
  Master essential gadmin commands for starting, stopping, configuring, and checking self-managed TigerGraph. Use when administering servers.
license: MIT
---
# Managing Services with gadmin

## When to use this
Use when administering self-managed TigerGraph servers, verifying service status, or applying configuration parameters.

## Prerequisites
TigerGraph server installation and terminal access. Links:
- [TigerGraph gadmin Reference](https://docs.tigergraph.com)

## Steps
1. Check the health status of all cluster services:
   ```bash
   gadmin status
   ```
2. Stop all database engine processes safely:
   ```bash
   gadmin stop -y
   ```
3. Start database services:
   ```bash
   gadmin start -y
   ```
4. View active service log file paths:
   ```bash
   gadmin log
   ```

## Common mistakes
- Killing service processes forcefully using standard Linux `kill -9` commands instead of using `gadmin stop`. Force-killing can corrupt active database segments.
- Modifying configuration parameters in configuration files directly; always use `gadmin config` commands.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
