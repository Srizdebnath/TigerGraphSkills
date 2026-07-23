---
name: algo-all-pairs-shortest-path
description: >
  Install and run All-Pairs Shortest Path in GSQL. Use when calculating routing matrix tables across all vertices.
license: MIT
---
# Running All-Pairs Shortest Path (APSP)

## When to use this
Use when calculating distances between all pairs of nodes to build path matrices, or computing network diameter.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the APSP query.
2. Run the query:
   ```gsql
   RUN QUERY tg_shortest_apsp(v_type="User", e_type="friend", wt_attr="weight", print_accum=FALSE, file_path="/tmp/apsp.csv")
   ```
3. Due to large output size, outputting to a file is highly recommended.

## Common mistakes
- Printing APSP output directly to the console on graphs with more than 1,000 vertices. The response size is O(V^2) and will crash the web server.
- Running APSP on large production instances, as it is extremely resource intensive.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
