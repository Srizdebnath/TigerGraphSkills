---
name: gsql-accumulators-advanced
description: >
  Utilize advanced accumulators (`HeapAccum`, `GroupByAccum`). Use when performing sorting, ranking, and complex grouping operations.
license: MIT
---
# Advanced GSQL Accumulators

## When to use this
Use when finding top-K records, sorting vertices by score during traversal, or grouping aggregated values across multi-dimensional criteria.

## Prerequisites
Knowledge of basic GSQL accumulator types. Links:
- [GSQL Accumulator Reference](https://docs.tigergraph.com)

## Steps
1. Declare a `HeapAccum` to store sorted, size-limited structures (top-K):
   ```gsql
   TYPEDEF TUPLE<name STRING, age INT> PersonTuple
   CREATE QUERY heap_accum() FOR GRAPH Social_Network {
       # Heap that stores top 3 oldest people, sorted descending by age
       HeapAccum<PersonTuple>(3, age DESC) @@top_oldest;
       
       Start = {User.*};
       Result = SELECT s FROM Start:s
                ACCUM @@top_oldest += PersonTuple(s.name, s.age);
       PRINT @@top_oldest;
   }
   ```
2. Declare a `GroupByAccum` for multi-dimensional aggregation:
   ```gsql
   GroupByAccum<STRING country, STRING status, SumAccum<INT> count> @@grouped_users;
   # Usage: @@grouped_users += (s.country, s.status -> 1);
   ```

## Common mistakes
- Forgetting to define a tuple when using `HeapAccum` for multi-attribute elements.
- Allocating very large limits to `HeapAccum` (e.g., K > 10000) inside local vertex accumulators. This leads to massive RAM overhead. Keep local HeapAccums minimal.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
