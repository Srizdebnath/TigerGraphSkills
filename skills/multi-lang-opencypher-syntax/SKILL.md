---
name: multi-lang-opencypher-syntax
description: >
  Translate openCypher query logic to high-performance GSQL queries. Use when refactoring migrated database queries.
license: MIT
---
# openCypher to GSQL Syntax Translation

## When to use this
Use when converting queries from Neo4j (Cypher) to TigerGraph (GSQL) to achieve production-grade speed and scalability.

## Prerequisites
Basic Cypher and GSQL syntax knowledge. Links:
- [GSQL Query Reference](https://docs.tigergraph.com)

## Steps
1. Map `MATCH (a)-[:rel]->(b)` to GSQL `SELECT` statement:
   ```gsql
   # openCypher:
   # MATCH (a:User)-[:friend]->(b:User) RETURN a.name, b.name
   
   # GSQL equivalent:
   Start = {User.*};
   Result = SELECT b FROM Start:a - (friend) - User:b;
   PRINT a.name, b.name;
   ```
2. Map Cypher aggregate operations to GSQL Accumulators (`SumAccum`, `MapAccum`).

## Common mistakes
- Attempting to do direct copy-paste translations. GSQL executes traversal steps in a vertex-parallel loop model, whereas Cypher is row-based. Refactor to leverage GSQL parallel accumulator logic.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
