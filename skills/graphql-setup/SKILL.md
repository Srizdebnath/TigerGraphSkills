---
name: graphql-setup
description: >
  Configure and start the GraphQL Service on TigerGraph. Use when exposing graph data schemas via standard GraphQL endpoints.
license: MIT
---
# Setting up the GraphQL Service

## When to use this
Use when application developers want to access TigerGraph data using standard GraphQL queries from mobile or frontend web apps.

## Prerequisites
Active TigerGraph Savanna workspace or Enterprise instance. Links:
- [GraphQL Service Documentation](https://docs.tigergraph.com)

## Steps
1. Enable the GraphQL service in your TigerGraph instance using GSQL/Admin Portal tools.
2. Configure the GraphQL Service settings, defining host bindings and port mappings (usually port 9000 or a specific GraphQL port).
3. Start the GraphQL service container/process.
4. Access the GraphQL playground/endpoint URL (e.g. `http://localhost:9000/graphql`).

## Common mistakes
- Assuming the GraphQL service is active by default. It must be explicitly configured and enabled in your instance settings.
- Exposing the GraphQL schema globally without setting up authentication headers.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
