---
name: gsql-schema-export
description: >
  Export the GSQL DDL schema definitions from a running TigerGraph instance. Use when copying schemas to new environments or checking in code.
license: MIT
---
# Exporting Graph Schema DDL

## When to use this
Use when migrating schema structures to production, or checking the current database state into a Git repository.

## Prerequisites
Access to GSQL CLI client. Links:
- [GSQL Command Reference](https://docs.tigergraph.com)

## Steps
1. Log in to the GSQL CLI client.
2. Export the entire database schema structure (includes vertex, edge, graph, and job definitions):
   ```bash
   gsql "EXPORT SCHEMA" > schema.gsql
   ```
3. Export schema for a specific graph:
   ```bash
   gsql -g StoreGraph "EXPORT SCHEMA" > store_schema.gsql
   ```
4. Examine the output GSQL script which can be run directly on another instance to recreate the structure.

## Common mistakes
- Confusing `EXPORT SCHEMA` with exporting the actual graph *data* (which is done via `EXPORT DATABASE` or ETL tools).
- Exporting system-level metadata that cannot be run on another cluster due to pathing or node count differences.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
