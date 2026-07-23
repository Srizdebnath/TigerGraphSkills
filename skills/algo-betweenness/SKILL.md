---
name: algo-betweenness
description: >
  Install and run Betweenness Centrality in GSQL. Use when finding bridge nodes or routing bottlenecks in graphs.
license: MIT
---
# Running Betweenness Centrality

## When to use this
Use when finding nodes that act as intermediaries or bridges between different communities, such as critical infrastructure junctions.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Deploy the betweenness centrality query code.
2. Execute the query:
   ```gsql
   RUN QUERY tg_betweenness_cent(v_type="User", e_type="friend", top_k=10, print_accum=TRUE, result_attr="betweenness", file_path="")
   ```
3. Node importance is calculated based on the count of shortest paths passing through it.

## Common mistakes
- Calculating exact betweenness on large graphs. Exact betweenness is O(V*E), which is very slow. Use approximate betweenness algorithms instead.
- Attempting to run on unconnected components without specifying traversal limits.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
