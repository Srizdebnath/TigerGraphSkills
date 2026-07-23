---
name: algo-jaccard-similarity
description: >
  Install and run Jaccard Similarity in GSQL. Use when measuring node neighborhood overlap and intersection similarity.
license: MIT
---
# Running Jaccard Similarity

## When to use this
Use when building recommendation systems based on shared items (e.g., users who purchased the same products).

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the Jaccard similarity query.
2. Run the query, comparing a target seed node to others:
   ```gsql
   RUN QUERY tg_jaccard_sub_target(source_vertex="User1", v_type="User", e_type="friend", top_k=10, print_accum=TRUE, file_path="")
   ```
3. Scores range from 0.0 (no shared neighbors) to 1.0 (identical neighbors).

## Common mistakes
- Attempting to calculate all-pairs Jaccard similarity on huge graphs. Limit similarity scoring to a target seed or filter comparison candidate sets.
- Counting duplicate edges if multiple edge types link the vertices; refine edge parameter lists.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
