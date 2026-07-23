---
name: gsql-perf-memory-tuning
description: >
  Configure query-level memory limits and prevent out-of-memory (OOM) failures. Use when tuning system performance.
license: MIT
---
# Tuning GSQL Query Memory Limits

## When to use this
Use when complex queries fail with out-of-memory errors or cause TigerGraph's engine to auto-abort tasks.

## Prerequisites
Access to `gadmin` configuration commands. Links:
- [TigerGraph Memory Management Docs](https://docs.tigergraph.com)

## Steps
1. Adjust query-level timeout limits using HTTP headers or `gadmin` settings:
   ```bash
   gadmin config set GSQL.QueryTimeoutSec 120
   ```
2. Set query memory thresholds using header properties on REST++ requests:
   ```bash
   curl -X GET -H "GSQL-TIMEOUT: 60" -H "GSQL-MEMORY-LIMIT: 4000" ...
   ```
3. Configure hard system-wide thresholds via `gadmin`:
   ```bash
   gadmin config set GSE.MaxMemoryGB 16
   gadmin config apply
   gadmin restart gse -y
   ```

## Common mistakes
- Increasing limits blindly without optimization. Raising memory limits on inefficient queries will only result in larger OOM crashes. Optimize loops first.
- Forgetting to apply config and restart service after running `gadmin config set`.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
