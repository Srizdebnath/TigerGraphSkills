---
name: devops-cluster-expansion
description: >
  Expand or shrink a self-managed TigerGraph cluster. Use when scaling computing nodes and partitioning database segments.
license: MIT
---
# Scaling and Cluster Expansion

## When to use this
Use when database size or queries/sec grow, requiring adding new physical machines to partition data (scaling out).

## Prerequisites
Additional server nodes with matching OS configurations, SSH setup. Links:
- [TigerGraph Installation Guide](https://docs.tigergraph.com)

## Steps
1. Install TigerGraph binaries on the new nodes.
2. Update the cluster configuration manifest file, detailing IPs and node mappings.
3. Run cluster expansion command using gadmin:
   ```bash
   gadmin cluster expand manifest.json
   ```
4. Wait for the data replication and redistribution process to complete, which copies data partition segments to new nodes.

## Common mistakes
- Scaling out on machines with unequal hardware resources. Distributed TigerGraph clusters perform at the speed of the slowest node.
- Executing cluster expansion during high transactional write loads.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
