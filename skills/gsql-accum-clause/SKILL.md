---
name: gsql-accum-clause
description: >
  Implement parallel aggregation using the GSQL ACCUM clause. Use when updating accumulators during edge traversals.
license: MIT
---
# Using the ACCUM Clause

## When to use this
Use when iterating over matching edges in a traversal to aggregate attributes, calculate weights, or flag visited nodes in parallel.

## Prerequisites
Basic understanding of SELECT statements and Accumulators. Links:
- [GSQL SELECT Reference](https://docs.tigergraph.com)

## Steps
1. Use the `ACCUM` clause inside a `SELECT` statement block to execute operations for every matching edge/path segment:
   ```gsql
   Start = {User.*};
   Result = SELECT t
            FROM Start:s - (friend:e) - User:t
            ACCUM s.@max_friend_age += t.age,      # Run on source vertex
                  t.@max_friend_age += s.age;      # Run on target vertex
   ```
2. Note that `ACCUM` runs in parallel across all threads, processing every traversed edge.

## Common mistakes
- Performing non-accumulator operations or modifications inside the `ACCUM` clause. Standard attributes cannot be written directly here; only accumulator updates (`+=`) are allowed.
- Assuming execution order inside `ACCUM`. Operations are parallelized and asynchronous; do not depend on serial execution.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
