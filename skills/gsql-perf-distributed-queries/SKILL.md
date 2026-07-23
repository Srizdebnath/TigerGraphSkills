---
name: gsql-perf-distributed-queries
description: >
  Write queries optimized for distributed TigerGraph clusters. Use when managing large-scale sharded databases.
license: MIT
---
# Optimizing Distributed GSQL Queries

## When to use this
Use when deploying TigerGraph in a multi-node, distributed cluster where data is sharded across multiple machines.

## Prerequisites
Multi-node cluster setup. Links:
- [GSQL Distributed Query Guide](https://docs.tigergraph.com)

## Steps
1. Write queries using the `DISTRIBUTED` keyword in the header if they require cross-node traversal:
   ```gsql
   CREATE DISTRIBUTED QUERY multi_node_query() FOR GRAPH Social_Network {
       ...
   }
   ```
2. Minimize cross-node hops (shuffling) by utilizing local vertex partitioning features.
3. Keep accumulator synchronization to a minimum by aggregating locally before broadcasting back to the coordinator node.

## Common mistakes
- Running non-distributed queries on a multi-node cluster, which limits execution to a single node and wastes the cluster's compute capacity.
- Designing schemas with high-degree hubs that require constant routing between physical machines, degrading network latency.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
