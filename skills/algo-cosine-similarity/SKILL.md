---
name: algo-cosine-similarity
description: >
  Install and run Cosine Similarity in GSQL. Use when measuring similarity of vertex feature vectors and edge weights.
license: MIT
---
# Running Cosine Similarity

## When to use this
Use when comparing items based on ratings, attributes, or numeric weights rather than binary existence of edges.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the Cosine similarity query.
2. Run the query:
   ```gsql
   RUN QUERY tg_cosine_sub_target(source_vertex="User1", v_type="User", e_type="rated", top_k=10, print_accum=TRUE, file_path="")
   ```

## Common mistakes
- Assuming Cosine similarity handles unweighted edges as effectively as Jaccard; Cosine is designed for weighted vectors.
- Not normalizing vector lengths before calculations if utilizing custom math.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
