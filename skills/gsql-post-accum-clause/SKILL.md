---
name: gsql-post-accum-clause
description: >
  Update vertex attributes and perform filtering using the GSQL POST-ACCUM clause. Use when computing vertex-level logic after traversals.
license: MIT
---
# Using the POST-ACCUM Clause

## When to use this
Use when you need to perform calculations on a per-vertex basis (not per-edge) using the accumulated values collected in the `ACCUM` phase.

## Prerequisites
Understanding GSQL ACCUM clauses. Links:
- [GSQL SELECT Reference](https://docs.tigergraph.com)

## Steps
1. Write the `POST-ACCUM` clause after the `ACCUM` clause in a `SELECT` block:
   ```gsql
   Start = {User.*};
   Result = SELECT s
            FROM Start:s - (friend) - User:t
            ACCUM s.@total_friend_age += t.age
            POST-ACCUM s.avg_friend_age = s.@total_friend_age / s.outdegree("friend");
   ```
2. Note that `POST-ACCUM` runs once per vertex in the result set, making it ideal for updating actual vertex attributes.

## Common mistakes
- Attempting to update a target vertex (`t`) attribute in `POST-ACCUM` if the select statement only exposes the source (`s`). The `POST-ACCUM` clause only iterates over the vertices matching the output of the query block.
- Confusing `ACCUM` (per-edge traversal processing) with `POST-ACCUM` (per-vertex result processing).

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
