---
name: gsql-accumulators-collection
description: >
  Declare and use collection accumulators (`ListAccum`, `SetAccum`, `BagAccum`, `MapAccum`). Use when collecting arrays, sets, and maps.
license: MIT
---
# Collection Accumulators in GSQL

## When to use this
Use when gathering structures (lists, unique sets, unordered collections, or key-value pairs) dynamically during traversals.

## Prerequisites
Familiarity with GSQL accumulators. Links:
- [GSQL Accumulator Reference](https://docs.tigergraph.com)

## Steps
1. Declare collection accumulators:
   ```gsql
   CREATE QUERY collection_accum() FOR GRAPH Social_Network {
       ListAccum<STRING> @@all_names;
       SetAccum<STRING> @friend_countries;
       MapAccum<STRING, INT> @@role_counts;
       
       Start = {User.*};
       Result = SELECT s FROM Start:s - (friend) - User:t
                ACCUM @@all_names += s.name,
                      s.@friend_countries += t.country,
                      @@role_counts += (t.role -> 1);
       PRINT @@all_names, @@role_counts;
   }
   ```
2. Note that `ListAccum` preserves order and duplicates, `SetAccum` guarantees uniqueness, `BagAccum` is unordered with duplicates, and `MapAccum` merges keys.

## Common mistakes
- Overusing `ListAccum` on highly connected vertices, which can cause excessive memory allocation. Use `SetAccum` or aggregate into maps/counts early.
- Forgetting that maps accumulate values of the same key using the `+=` operator (e.g., if value is `INT`, they sum; if list, they append).

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
