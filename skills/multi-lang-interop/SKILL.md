---
name: multi-lang-interop
description: >
  Integrate and run queries using GSQL, openCypher, and GQL on the same graph database. Use when sharing data schema views.
license: MIT
---
# GSQL, openCypher, and GQL Interoperability

## When to use this
Use when a team utilizes multiple query standards and needs to combine results or run comparative performance operations.

## Prerequisites
TigerGraph Savanna workspace. Links:
- [TigerGraph Savanna Documentation](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. Define the unified graph schema using standard GSQL DDL.
2. Query the exact same schema structure using GSQL queries for complex accumulative reporting, openCypher for quick lookups, and GQL for standard reporting.
3. Note that updates made by one language are instantly visible to query engines of the others.

## Common mistakes
- Mismatching label names. openCypher uses capitalized labels (e.g. `:User`) which maps directly to the case-sensitive GSQL vertex name (`User`). Keep case consistent.
- Expecting GSQL-specific accumulators to be written inside openCypher queries.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
