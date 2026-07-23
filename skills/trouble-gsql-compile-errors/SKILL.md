---
name: trouble-gsql-compile-errors
description: >
  Diagnose and fix common GSQL compilation and syntax errors. Use when query installations or schema changes fail.
license: MIT
---
# Fixing GSQL Compiler Errors

## When to use this
Use when query compilation or schema changes fail with syntax errors, undeclared accumulators, or type mismatches.

## Prerequisites
Completed query save/compile run. Links:
- [GSQL Query Reference](https://docs.tigergraph.com)

## Steps
1. Inspect the compiler error message, noting the line number and column.
2. Check for common issues: missing semicolons, using single `@` instead of double `@@` on global variables, or calling non-existent attributes.
3. Run a semantic check using interpreted execution mode (`INTERPRET QUERY`) to verify logic flows without compiling.
4. Fix type casting issues (e.g., using `to_string()` or `to_int()` where required).

## Common mistakes
- Attempting to update vertex fields directly inside the `ACCUM` clause instead of using local accumulators, which triggers compilation errors.
- Forgetting that all vertices and edges in query paths must be defined in the active schema.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
