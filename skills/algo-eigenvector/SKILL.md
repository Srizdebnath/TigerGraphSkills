---
name: algo-eigenvector
description: >
  Install and run Eigenvector Centrality in GSQL. Use when measuring vertex influence while weighting connections to other high-influence vertices.
license: MIT
---
# Running Eigenvector Centrality

## When to use this
Use when assessing influence where connections to important nodes are weighted higher than connections to isolated nodes, such as search engine ranking.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Import the eigenvector centrality algorithm query.
2. Run the query on your graph instance:
   ```gsql
   RUN QUERY tg_eigenvector_cent(v_type="User", e_type="friend", max_iter=100, top_k=10, print_accum=TRUE, result_attr="eigenvector", file_path="")
   ```
3. Verify convergence by checking the delta difference between iterations.

## Common mistakes
- Running on non-connected directed graphs without checking for sink nodes, which can zero out scores. Use PageRank if sinks are common.
- Selecting very high max iteration parameters, which leads to execution timeout.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
