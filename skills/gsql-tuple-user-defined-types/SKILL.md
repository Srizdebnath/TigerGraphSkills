---
name: gsql-tuple-user-defined-types
description: >
  Define and use user-defined tuples (composite attribute structures) in GSQL schemas. Use when storing structured data inside vertices or edges.
license: MIT
---
# User-Defined Tuples in GSQL Schema

## When to use this
Use when you need to group related attributes into a single reusable structure, such as an address or custom statistics, inside a vertex attribute.

## Prerequisites
Basic vertex and DDL understanding. Links:
- [GSQL Tuple Reference](https://docs.tigergraph.com)

## Steps
1. Define the tuple type at the global level:
   ```gsql
   TYPEDEF TUPLE <street STRING, city STRING, zip INT> AddressTuple
   ```
2. Reference the tuple type as an attribute type inside your vertex or edge:
   ```gsql
   CREATE VERTEX User (PRIMARY_ID username STRING, address AddressTuple, contacts LIST<STRING>) WITH stats="OUTDEGREE_BY_EDGETYPE";
   ```
3. Initialize or assign tuples inside queries using the tuple constructor:
   ```gsql
   AddressTuple("123 Main St", "San Jose", 95113)
   ```

## Common mistakes
- Overusing tuples for relationships. If the tuple represents another entity that should be traversable, model it as a vertex and edge, not a tuple attribute.
- Forgetting that tuple fields cannot be indexed individually for global search.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
