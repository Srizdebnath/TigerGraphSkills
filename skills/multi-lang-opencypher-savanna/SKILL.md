---
name: multi-lang-opencypher-savanna
description: >
  Write and execute openCypher queries on TigerGraph Savanna. Use when migrating query code or leveraging pattern matching.
license: MIT
---
# Running openCypher on TigerGraph

## When to use this
Use when developers familiar with openCypher or Neo4j syntax want to run queries on TigerGraph without writing native GSQL.

## Prerequisites
TigerGraph Savanna workspace (v4.x+). Links:
- [TigerGraph Savanna Documentation](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. Open the GSQL Web Shell or query editor in TigerGraph Savanna.
2. Write your openCypher query utilizing Cypher syntax:
   ```cypher
   MATCH (u:User)-[:friend]->(f:User)
   WHERE u.age > 30
   RETURN u.name, f.name
   ```
3. Run the query directly via the interpreted endpoint or CLI.

## Common mistakes
- Attempting to use openCypher features on legacy TigerGraph 3.x instances. This feature is natively supported in the newer v4.x/Savanna cloud engines.
- Expecting complex, multi-statement transactional Cypher writes to execute with the same speed as GSQL custom loading jobs.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
