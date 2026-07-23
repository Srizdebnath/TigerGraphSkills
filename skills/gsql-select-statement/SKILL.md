---
name: gsql-select-statement
description: >
  Master GSQL SELECT query blocks, FROM, and WHERE clauses. Use when filtering vertices and traversing edge relationships.
license: MIT
---
# The GSQL SELECT Statement

## When to use this
Use when retrieving, filtering, and joining vertex sets through edge hops inside GSQL queries.

## Prerequisites
GSQL query creation basics. Links:
- [GSQL SELECT Reference](https://docs.tigergraph.com)

## Steps
1. Basic single-hop SELECT statement structure:
   ```gsql
   Start = {User.*};
   Result = SELECT t
            FROM Start:s - (friend:e) - User:t
            WHERE s.age > 21 AND t.status == "active";
   ```
2. Label elements in the path: `:s` for source vertex, `:e` for edge, and `:t` for target vertex.
3. Use wildcards (`_`) if the edge type or target vertex type is dynamic:
   ```gsql
   Result = SELECT t FROM Start:s - (:e) - _:t;
   ```

## Common mistakes
- Assuming GSQL `SELECT` works like relational SQL. GSQL `SELECT` acts as a parallel graph traversal filter step, where the output is a set of vertices, not a flat table.
- Not declaring alias variables for source/target, preventing attribute retrieval in subsequent clauses.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
