---
name: graphql-schema-generation
description: >
  Generate and customize GraphQL schemas from TigerGraph DDL definitions. Use when mapping graph models to GraphQL types.
license: MIT
---
# GraphQL Schema Generation

## When to use this
Use when mapping vertex and edge definitions to GraphQL schemas to control which properties are queryable.

## Prerequisites
Active GraphQL Service. Links:
- [GraphQL Service Documentation](https://docs.tigergraph.com)

## Steps
1. Access the schema generation endpoint of your GraphQL Service.
2. The system automatically inspects active GSQL schemas and maps:
   - Vertex Types to GraphQL Object Types
   - Edge Types to Nested GraphQL Fields
3. Customize schema generation rules using a configuration JSON, naming exclusions, and setting read-only parameters.

## Common mistakes
- Exposing internal system vertices in the public GraphQL schema. Exclude administrative models using filter configurations.
- Forgetting to refresh the GraphQL schema after performing online GSQL schema changes.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
