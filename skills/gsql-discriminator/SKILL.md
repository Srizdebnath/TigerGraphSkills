---
name: gsql-discriminator
description: >
  Implement composite keys and discriminator types in GSQL schema design. Use when modeling multi-column unique identifiers.
license: MIT
---
# Using Discriminator and Composite Keys

## When to use this
Use when entities are uniquely identified by a combination of multiple attributes rather than a single string or integer.

## Prerequisites
Familiarity with standard vertex definitions. Links:
- [GSQL DDL Keys Documentation](https://docs.tigergraph.com)

## Steps
1. Define a vertex type with multiple attributes making up the primary key:
   ```gsql
   CREATE VERTEX Account (id STRING, country_code STRING, status STRING, PRIMARY_ID (id, country_code)) WITH stats="OUTDEGREE_BY_EDGETYPE";
   ```
2. When importing or querying this vertex, reference both values as a tuple or composite type.
3. The system will automatically combine these fields internally to form the primary lookup index.

## Common mistakes
- Concatenating composite fields manually as strings (e.g., `id + "_" + country_code`) which wastes space and adds runtime CPU overhead. Use native composite `PRIMARY_ID` instead.
- Forgetting that all parts of a composite primary key must be provided during data loading.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
