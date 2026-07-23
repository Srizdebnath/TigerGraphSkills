---
name: algo-closeness
description: >
  Install and run Closeness Centrality in GSQL. Use when measuring how close a vertex is to all other vertices in a network.
license: MIT
---
# Running Closeness Centrality

## When to use this
Use when measuring the time or distance it takes to spread information from a specific node to other nodes, such as resource routing.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the closeness centrality algorithm query from the library.
2. Run the closeness centrality query on your graph schema:
   ```gsql
   RUN QUERY tg_closeness_cent(v_type="User", e_type="friend", top_k=10, print_accum=TRUE, result_attr="closeness", file_path="")
   ```
3. Closeness score is computed as the reciprocal of the sum of shortest path distances to all other nodes.

## Common mistakes
- Running Closeness Centrality on huge graphs (10M+ nodes) directly. The computational complexity is high, so restrict to smaller graphs or run on subgraphs.
- Assuming undirected traversals work on one-way directed edges. Choose edge parameters that match physical schema connectivity.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
