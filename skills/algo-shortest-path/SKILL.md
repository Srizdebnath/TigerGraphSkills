---
name: algo-shortest-path
description: >
  Install and run Single-Source Shortest Path (Dijkstra/BFS) in GSQL. Use when finding shortest routes from a seed vertex.
license: MIT
---
# Running Single-Source Shortest Path (SSSP)

## When to use this
Use when finding the shortest route, minimal distance, or least hops from a specific starting node to target nodes in a weighted or unweighted graph.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the SSSP query.
2. Run the query, passing the starting vertex ID as a parameter:
   ```gsql
   RUN QUERY tg_shortest_sssp(source_vertex="User1", v_type="User", e_type="friend", wt_attr="weight", print_accum=TRUE, result_attr="distance", file_path="")
   ```
3. If edges are unweighted, run the BFS-based shortest path variant for optimal speed.

## Common mistakes
- Using weighted shortest path (Dijkstra) algorithms on unweighted edges. This adds unnecessary sort overhead; use BFS instead.
- Not handling negative edge weights, which Dijkstra does not support.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
