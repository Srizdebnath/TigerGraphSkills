---
name: migration-neo4j-tigergraph
description: >
  Migrate schema, Cypher queries, and graph data from Neo4j to TigerGraph. Use when translating Cypher match logic to GSQL.
license: MIT
---
# Migrating from Neo4j to TigerGraph

## When to use this
Use when migrating graph database systems from Neo4j to TigerGraph to achieve parallel traversal speed and massive scalability.

## Prerequisites
Neo4j schema and Cypher query files. Links:
- [GSQL Language Reference](https://docs.tigergraph.com)

## Steps
1. Map Neo4j node labels to TigerGraph Vertex types and Neo4j relationship types to TigerGraph Edge types.
2. Define GSQL schemas using GSQL DDL statements (remember that TigerGraph requires schemas to be defined, unlike Neo4j's schema-free models).
3. Export Neo4j data as CSV files using APOC or ETL tools.
4. Write GSQL Loading Jobs to ingest CSV files.
5. Translate Cypher query MATCH statements to GSQL SELECT statement blocks.

## Common mistakes
- Expecting schema-free behaviors. TigerGraph is strongly typed; you must define all vertex and edge properties in the schema beforehand.
- Directly copying Cypher MATCH statements into GSQL; translate Cypher to vertex-parallel GSQL accumulator loops.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
