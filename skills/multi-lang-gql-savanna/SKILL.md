---
name: multi-lang-gql-savanna
description: >
  Execute ISO GQL queries on TigerGraph Savanna. Use when implementing standard graph query language standards.
license: MIT
---
# Using ISO GQL Standard on Savanna

## When to use this
Use when standardizing database querying on the ISO/IEC 39075 GQL specification for interoperability.

## Prerequisites
TigerGraph Savanna instance. Links:
- [TigerGraph Savanna Release Notes](https://docs.tigergraph.com/savanna/main/overview/release-notes)

## Steps
1. Log in to the Savanna query editor.
2. Execute standard GQL pattern-matching queries:
   ```gql
   MATCH (u:User WHERE age > 21)-[:friend]->(f:User)
   RETURN u.name, f.name
   ```
3. Retrieve results in standard graph format.

## Common mistakes
- Conflating GQL (the database query language standard) with GraphQL (the API querying format). They are completely distinct.
- Assuming all GSQL accumulator functions are available inside standard GQL. Complex calculations still require GSQL.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/release-notes](https://docs.tigergraph.com/savanna/main/overview/release-notes)
