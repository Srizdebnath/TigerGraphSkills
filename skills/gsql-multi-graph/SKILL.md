---
name: gsql-multi-graph
description: >
  Configure multi-graph schemas in TigerGraph. Use when separating data boundaries, or sharing global/local vertex and edge types.
license: MIT
---
# Creating and Managing Multiple Graphs

## When to use this
Use when multiple departments or applications share the same physical cluster but require separate logical graph boundaries and access control.

## Prerequisites
Administrative permissions on TigerGraph Enterprise. Links:
- [Multi-Graph DDL Documentation](https://docs.tigergraph.com)

## Steps
1. Create global vertices and edges (available to all graphs):
   ```gsql
   CREATE VERTEX Product (PRIMARY_ID pid STRING, name STRING) WITH stats="OUTDEGREE_BY_EDGETYPE";
   ```
2. Create logical graphs referencing specific vertex and edge types:
   ```gsql
   CREATE GRAPH StoreGraph (User, Product, purchase);
   CREATE GRAPH MarketingGraph (User, friend);
   ```
3. Switch to a specific graph context before running commands:
   ```gsql
   USE GRAPH StoreGraph
   ```

## Common mistakes
- Modifying global vertex/edge definitions without realizing it affects all graphs referencing them.
- Conflating graph-specific vertex/edge lists with namespaces; a vertex/edge can belong to multiple graphs.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
