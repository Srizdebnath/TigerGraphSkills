---
name: trouble-query-timeout
description: >
  Optimize and resolve GSQL query timeouts and memory overuse. Use when traversals run out of time or trigger OOMs.
license: MIT
---
# Fixing Query Timeout and Memory Errors

## When to use this
Use when query execution runs longer than allowed limits (returns HTTP 504 / REST-3001) or gets aborted by the engine.

## Prerequisites
Slow-running query. Links:
- [GSQL Performance Tuning](https://docs.tigergraph.com)

## Steps
1. Add a timeout header limit to test REST requests:
   ```bash
   curl -X GET -H "GSQL-TIMEOUT: 180" ...
   ```
2. Profile the query to find the bottleneck traversal hop.
3. Add `LIMIT` clauses to intermediate traversals to cap set sizes.
4. Replace heavy collection accumulators with simple scalars to reduce RAM consumption.

## Common mistakes
- Increasing GSQL system timeout settings infinitely without optimizing the traversal logic. This can lead to system-wide thread starvation.
- Scanning the full graph inside nested loops.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
