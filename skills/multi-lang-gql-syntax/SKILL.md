---
name: multi-lang-gql-syntax
description: >
  Translate ISO GQL queries to GSQL query syntax. Use when converting standard database queries to custom high-performance queries.
license: MIT
---
# GQL to GSQL Syntax Translation

## When to use this
Use when converting standard-based ISO GQL statements to GSQL queries to utilize advanced scripting and looping.

## Prerequisites
ISO GQL standard understanding. Links:
- [GSQL Query Reference](https://docs.tigergraph.com)

## Steps
1. Identify the matching path structures in GQL.
2. Rebuild the logic inside a GSQL query block, translating `MATCH` filters into `SELECT ... WHERE` and `ACCUM` structures.
3. Utilize standard accumulators to manage any complex aggregations defined in GQL return clauses.

## Common mistakes
- Overcomplicating simple GQL queries. GSQL matches simple single-hop traversals with very high efficiency, so maintain simple query hops.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
