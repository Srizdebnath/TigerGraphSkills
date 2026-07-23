---
name: gsql-accumulators-basic
description: >
  Understand and use basic global and local accumulators (`SumAccum`, `MaxAccum`, etc.). Use when performing parallel graph aggregations.
license: MIT
---
# Basic GSQL Accumulators

## When to use this
Use when aggregating numeric values (sum, max, min) or boolean flags (or, and) across vertices in parallel traversals.

## Prerequisites
Basic GSQL query knowledge. Links:
- [GSQL Accumulator Docs](https://docs.tigergraph.com)

## Steps
1. Declare local accumulators (prefixed with `@`) to store data on individual vertices, or global accumulators (prefixed with `@@`) for graph-wide aggregates:
   ```gsql
   CREATE QUERY basic_accum() FOR GRAPH Social_Network {
       SumAccum<INT> @@total_age;
       MaxAccum<INT> @max_friend_age;
       
       Start = {User.*};
       Result = SELECT s FROM Start:s - (friend) - User:t
                ACCUM @@total_age += t.age,
                      s.@max_friend_age += t.age;
       PRINT @@total_age;
   }
   ```
2. Basic types: `SumAccum<T>`, `MaxAccum<T>`, `MinAccum<T>`, `OrAccum`, `AndAccum`.

## Common mistakes
- Forgetting that local accumulators must be prefixed with a single `@` and global accumulators with double `@@`.
- Expecting standard variables (e.g. `INT x = 0;`) to aggregate in parallel query blocks. Standard variables are not thread-safe; you must use accumulators.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
