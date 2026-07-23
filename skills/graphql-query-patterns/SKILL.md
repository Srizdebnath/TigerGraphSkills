---
name: graphql-query-patterns
description: >
  Write and run GraphQL queries against TigerGraph. Use when executing nested traversals and filtering records via API.
license: MIT
---
# Querying Graph Data via GraphQL

## When to use this
Use when client applications query specific fields, nesting relationships, and limiting return payloads dynamically.

## Prerequisites
Running GraphQL Service. Links:
- [GraphQL Service Documentation](https://docs.tigergraph.com)

## Steps
1. Format your GraphQL query, requesting nested fields:
   ```graphql
   query {
     user(username: "Alice") {
       name
       age
       friend {
         name
       }
     }
   }
   ```
2. Send the query as a POST payload to the `/graphql` endpoint.
3. Retrieve the structured JSON response mirroring the requested structure.

## Common mistakes
- Requesting deeply nested relationships (e.g., 5+ hops) in a single GraphQL query without limits, causing performance spikes on the TigerGraph database.
- Mismatched scalar type casting in query variables.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
