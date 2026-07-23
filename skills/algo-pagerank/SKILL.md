---
name: algo-pagerank
description: >
  Install and run the PageRank algorithm in GSQL. Use when measuring vertex importance and influence based on incoming link structures.
license: MIT
---
# Running PageRank Centrality

## When to use this
Use when finding the most influential nodes in a network, such as key accounts, web pages, or central entities in social graphs.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Import the PageRank algorithm from the GSQL Graph Algorithm Library.
2. Call or execute the query: 
   ```gsql
   RUN QUERY tg_pagerank(v_type="User", e_type="friend", max_change=0.001, max_iter=20, damping=0.85, top_k=10, print_accum=TRUE, result_attr="pagerank", file_path="")
   ```
3. Verify output returns top K vertices with their PageRank score.

## Common mistakes
- Running PageRank on very large graphs without setting `top_k` or outputting to a file, causing REST response overflow.
- Not handling convergence parameters correctly (e.g. setting max change limit too low, causing query timeouts).

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
