---
name: algo-label-propagation
description: >
  Install and run Label Propagation for community detection. Use when grouping vertices based on neighboring majority votes.
license: MIT
---
# Running Label Propagation

## When to use this
Use when performing fast, near-linear-time community partitioning on large graphs where Louvain might be too resource-intensive.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Import the label propagation algorithm query.
2. Run the query, passing iteration thresholds:
   ```gsql
   RUN QUERY tg_label_prop(v_type="User", e_type="friend", max_iter=10, print_accum=TRUE, result_attr="community_id", file_path="")
   ```
3. Verify vertices are assigned a community ID matching their dense cluster.

## Common mistakes
- Running too many iterations, which can cause community sizes to converge into a single huge community. Keep iterations under 15.
- Forgetting that Label Propagation is non-deterministic and can produce different clusters across separate runs.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
