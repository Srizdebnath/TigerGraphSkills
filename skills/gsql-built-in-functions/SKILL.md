---
name: gsql-built-in-functions
description: >
  Use GSQL built-in string, datetime, math, and conversion functions. Use when parsing and formatting query parameters.
license: MIT
---
# Built-In GSQL Functions

## When to use this
Use when manipulating text strings, calculating time durations, running mathematical functions, or casting types inside GSQL statements.

## Prerequisites
GSQL query creation. Links:
- [GSQL Query Reference](https://docs.tigergraph.com)

## Steps
1. String functions: `lower()`, `upper()`, `gsql_concat()`, `trim()`, `substr()`.
2. Datetime functions: `now()`, `datetime_to_epoch()`, `epoch_to_datetime()`, `datetime_add()`:
   ```gsql
   DATETIME cutoff = datetime_add(now(), INTERVAL -30 DAY);
   ```
3. Conversion functions: `to_string()`, `to_int()`, `to_float()`.
4. Call them directly inside filter and calculation blocks.

## Common mistakes
- Confusing GSQL string functions with standard C++ string methods. GSQL has specific SQL-like built-in signatures.
- Running heavy string concatenation operations inside parallel `ACCUM` loops. Keep heavy formatting in `POST-ACCUM` or client-side.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
