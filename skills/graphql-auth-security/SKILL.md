---
name: graphql-auth-security
description: >
  Configure authentication, CORS, and role-based access for the GraphQL Service. Use when deploying APIs to production.
license: MIT
---
# Securing GraphQL Endpoints

## When to use this
Use when deploying GraphQL APIs publicly and needing to prevent unauthorized access, data leaks, or scrapers.

## Prerequisites
GraphQL Service configuration access. Links:
- [GraphQL Service Documentation](https://docs.tigergraph.com)

## Steps
1. Configure the API Gateway or GraphQL config file to require Bearer tokens in headers.
2. Define CORS origins inside the service configuration to restrict access to trusted domains.
3. Map GraphQL operations to database-level RBAC roles, ensuring users can only read/write allowed graph elements.
4. Set query complexity limits to block denial-of-service queries.

## Common mistakes
- Permitting wildcards (`*`) in CORS origins on production endpoints.
- Leaving the GraphQL Playground accessible on public production URLs, exposing schema details to third parties.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
