---
name: algo-louvain
description: >
  Install and run the Louvain community detection algorithm. Use when maximizing modularity to partition graphs into communities.
license: MIT
---
# Running Louvain Community Detection

## When to use this
Use when finding hierarchical community structures and modular groups in complex graphs, such as fraud rings or interest groups.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the Louvain query from the algorithm library.
2. Execute the Louvain modularity optimization query:
   ```gsql
   RUN QUERY tg_louvain(v_type="User", e_type="friend", max_iter=10, print_accum=TRUE, result_attr="louvain_id", file_path="")
   ```
3. Note that the algorithm runs in iterations to optimize community grouping dynamically.

## Common mistakes
- Expecting instantaneous completion on graphs with highly connected hubs. Louvain requires significant internal message shuffling.
- Forgetting that edge weights are supported and should be parameterized if relationships contain strengths.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
