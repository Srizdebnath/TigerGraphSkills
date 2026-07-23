---
name: algo-connected-components
description: >
  Install and run Weakly/Strongly Connected Components. Use when finding isolated subgraphs and reachable node groups.
license: MIT
---
# Running Connected Components

## When to use this
Use when auditing database connectivity, identifying isolated islands, or classifying unreachable data partitions.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Import the weakly connected components (WCC) query from the library.
2. Run the query:
   ```gsql
   RUN QUERY tg_wcc(v_type="User", e_type="friend", print_accum=TRUE, result_attr="wcc_id", file_path="")
   ```
3. For directed reachability, use the Strongly Connected Components (SCC) algorithm query instead.

## Common mistakes
- Assuming WCC checks direction. Weakly Connected Components treats edges as undirected; if edge direction matters, you must use SCC.
- Trying to print the entire component structure to the screen on massive graphs; set the print parameter to false and output to attributes or files instead.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
