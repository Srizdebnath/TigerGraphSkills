---
name: algo-random-projection
description: >
  Install and run Fast Random Projection in GSQL. Use when generating low-dimensional node embeddings from graph structures.
license: MIT
---
# Running Fast Random Projection

## When to use this
Use when creating graph features (embeddings) to feed downstream machine learning models or clustering systems.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the random projection query.
2. Run the query, specifying output dimension sizes:
   ```gsql
   RUN QUERY tg_fast_rp(v_type="User", e_type="friend", dimension=128, print_accum=FALSE, result_attr="embedding", file_path="")
   ```
3. The generated embedding vector is saved directly to the vertex attribute.

## Common mistakes
- Trying to store high-dimensional float arrays (e.g. 512 dimensions) inside simple string attributes. Ensure the schema has a `LIST<DOUBLE>` or compress the output.
- Setting dimensions too large for the available RAM sizes.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
