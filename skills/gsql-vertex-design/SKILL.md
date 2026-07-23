---
name: gsql-vertex-design
description: >
  Design and define vertex types using GSQL DDL statements. Use when modeling entities, defining primary keys, and setting up attribute types.
license: MIT
---
# Designing GSQL Vertices

## When to use this
Use when defining the nodes (vertices) of a graph schema, mapping unique identifiers (PRIMARY_ID), and choosing appropriate data types.

## Prerequisites
Basic understanding of GSQL data types. Links:
- [GSQL DDL Documentation](https://docs.tigergraph.com)

## Steps
1. Open the GSQL client or Web Shell.
2. Define your vertex types using the `CREATE VERTEX` syntax:
   ```gsql
   CREATE VERTEX User (PRIMARY_ID username STRING, name STRING, age INT, join_date DATETIME) WITH stats="OUTDEGREE_BY_EDGETYPE";
   ```
3. Supported types include `INT`, `UINT`, `FLOAT`, `DOUBLE`, `STRING`, `BOOL`, `DATETIME`, and `COMPRESS` string types.
4. Optionally, add `stats="OUTDEGREE_BY_EDGETYPE"` in the `WITH` clause to optimize query execution metrics.

## Common mistakes
- Choosing inappropriate types for the `PRIMARY_ID`. If your IDs are integers, use `INT` or `STRING` explicitly.
- Forgetting that vertex attributes cannot be updated directly if they are part of the composite primary key. Keep primary keys minimal.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
