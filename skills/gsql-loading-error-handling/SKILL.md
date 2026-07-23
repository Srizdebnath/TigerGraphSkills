---
name: gsql-loading-error-handling
description: >
  Troubleshoot and fix GSQL loading job errors, reject files, and log outputs. Use when data imports fail, skip rows, or result in formatting errors.
license: MIT
---
# Troubleshooting Ingestion & Loading Errors

## When to use this
Use when data ingestion jobs fail, skip lines, throw type mismatch errors, or fail to upsert vertices/edges.

## Prerequisites
Completed run of a GSQL loading job. Links:
- [GSQL Loading Diagnostics](https://docs.tigergraph.com)

## Steps
1. Run your loading job and inspect the console summary output.
2. Locate rejected rows in the reject log path displayed at the end of the output (typically under `~/.tigergraph/log/gsql/` or workspace logs).
3. Use `gsql` commands to check the loader service status if the system hangs:
   ```bash
   gadmin status
   ```
4. Examine standard loading issues: header mismatches, missing values in composite primary keys, incorrect date formats (default format is `%Y-%m-%d %H:%M:%S`).

## Common mistakes
- Ignoring the return stats of the load. A job may return exit status 0 (Success) even if 90% of rows were rejected. Always verify the 'Success Records' count.
- Assuming empty strings are automatically parsed as NULL. Define default values in schema or handle them in the loading job mapping.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
