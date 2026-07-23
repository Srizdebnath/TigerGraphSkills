---
name: gsql-perf-accumulator-choice
description: >
  Choose and use GSQL accumulators efficiently. Use when tuning queries to reduce memory footprint and execution times.
license: MIT
---
# Optimizing Accumulator Performance

## When to use this
Use during performance profiling of query bottlenecks, specifically when memory usage spikes or execution is slow due to large datasets.

## Prerequisites
Basic understanding of GSQL accumulators. Links:
- [GSQL Performance Tuning](https://docs.tigergraph.com)

## Steps
1. Prefer `SumAccum<INT>` or `MaxAccum<INT>` over collections where possible.
2. Avoid allocating large `ListAccum` on highly connected 'supernodes'. Supernodes with 1M+ edges will crash memory if gathering a list.
3. Replace `SetAccum` with `MapAccum<T, BOOL>` if you need key checking, or use integer sums if only counting uniqueness is required.
4. If building top-K, configure `HeapAccum` with a tight size limit (e.g. 10 or 100) instead of collecting all records and sorting afterwards.

## Common mistakes
- Storing huge objects/vertices directly in collections. Store only the vertex primary key (`STRING`) or necessary scalar attributes instead of the entire vertex object.
- Using local accumulators where a single global accumulator could summarize the data with far less memory mapping.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
