---
name: devops-recovery-failure
description: >
  Troubleshoot node failure and configure automatic recovery in self-managed clusters. Use when diagnosing cluster partitions.
license: MIT
---
# Node Failure and Automatic Recovery

## When to use this
Use when a node in a distributed cluster goes offline, resulting in database status changing to degraded or down.

## Prerequisites
Multi-node cluster setup. Links:
- [TigerGraph Installation Guide](https://docs.tigergraph.com)

## Steps
1. Check cluster status to identify the failed node:
   ```bash
   gadmin status
   ```
2. Inspect the failed node log files (e.g. `gse.log` or `gpe.log`) to identify crashes.
3. If hardware failed, replace node, update SSH configs, and run repair commands:
   ```bash
   gadmin cluster repair <node_id>
   ```
4. TigerGraph will resync partition snapshots from replica nodes to restore online state.

## Common mistakes
- Attempting database repair without verifying if replicas have fully consistent states.
- Confusing network splits (split-brain) with hardware death; verify network ping connectivity first.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
