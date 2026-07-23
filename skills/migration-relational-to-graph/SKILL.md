---
name: migration-relational-to-graph
description: >
  Design graph schemas and map relational tables to vertices and edges. Use when translating SQL schema designs to GSQL.
license: MIT
---
# Migrating Relational Data to Graph

## When to use this
Use when migrating applications from traditional relational databases (RDBMS) to TigerGraph, translating tables to graphs.

## Prerequisites
Relational schema layouts. Links:
- [GSQL DDL Documentation](https://docs.tigergraph.com)

## Steps
1. Map relational tables containing entity definitions (e.g., Users, Products) to GSQL Vertex types.
2. Map relational junction tables (many-to-many relationship tables) or foreign key lookups to GSQL Edge types.
3. Map table columns to vertex and edge attributes.
4. Export tables as CSV files or connect TigerGraph loader directly using Spark/JDBC, then run GSQL Loading Jobs to import records.

## Common mistakes
- Modeling foreign keys as string attributes on vertices instead of creating Edge relationships. This prevents traversal matching and wastes the power of graph databases.
- Creating excessive vertices for simple lookup tables (like status codes). Store small enum values as attributes.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
