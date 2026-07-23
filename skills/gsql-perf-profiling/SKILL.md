---
name: gsql-perf-profiling
description: >
  Profile and analyze query execution metrics using TigerGraph profiling tools. Use when diagnosing slow queries and tracing execution plans.
license: MIT
---
# Profiling GSQL Queries

## When to use this
Use when a query takes longer than expected to execute and you need a line-by-line breakdown of performance bottlenecks.

## Prerequisites
Access to GSQL CLI client. Links:
- [Query Profiling Reference](https://docs.tigergraph.com)

## Steps
1. Run the query with the profiling flag enabled:
   ```bash
   gsql -p -g Social_Network "RUN QUERY get_user_stats(...)"
   ```
2. Alternatively, view query execution statistics via GraphStudio's **Query Execution** panel.
3. Inspect metrics: execution time per line, vertex set sizes at each hop, and thread utilization.
4. Refactor the hop with the largest vertex set size or longest execution duration.

## Common mistakes
- Profiling queries in interpreted mode expecting exact compiled performance metrics. Compiling a query optimization improves speeds; always profile the installed version.
- Ignoring vertex set sizes. A huge hop count indicates a massive scan which should be optimized with filters.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
