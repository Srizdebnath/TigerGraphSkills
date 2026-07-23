---
name: graphql-mutations
description: >
  Insert, update, and delete vertices and edges using GraphQL Mutations. Use when writing graph data via GraphQL APIs.
license: MIT
---
# GraphQL Mutations in TigerGraph

## When to use this
Use when client web/mobile applications need to create users, update profile attributes, or link nodes via GraphQL mutations.

## Prerequisites
Running GraphQL Service with write access enabled. Links:
- [GraphQL Service Documentation](https://docs.tigergraph.com)

## Steps
1. Formulate a mutation query to create a vertex:
   ```graphql
   mutation {
     createUser(username: "Bob", name: "Robert", age: 30) {
       username
       name
     }
   }
   ```
2. Formulate a mutation to link vertices with an edge:
   ```graphql
   mutation {
     createFriendship(from: "Alice", to: "Bob") {
       from
       to
     }
   }
   ```
3. Execute the payload and check success responses.

## Common mistakes
- Expecting complex GSQL accumulative operations to trigger inside basic CRUD mutations. Mutations are for simple writes; use GSQL queries for complex logic.
- Running batch inserts via individual GraphQL mutation calls. Use bulk REST++ loading jobs for large datasets instead.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
