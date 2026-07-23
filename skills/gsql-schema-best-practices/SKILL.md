---
name: gsql-schema-best-practices
description: >
  Best practices for GSQL graph schema modeling. Use when designing high-performance graph databases and avoiding performance traps.
license: MIT
---
# Graph Modeling Best Practices

## When to use this
Use during the initial design phase of a TigerGraph application to optimize query latency, data loading speeds, and memory consumption.

## Prerequisites
Basic understanding of graph theory and TigerGraph architecture. Links:
- [TigerGraph Schema Best Practices](https://docs.tigergraph.com)

## Steps
1. Keep vertices as the primary entities (nouns) and edges as the relations/actions (verbs).
2. Use directed edges with reverse edges (`WITH REVERSE_EDGE="..."`) rather than undirected edges if queries naturally traverse mostly in one direction.
3. Keep edge attribute sizes to a minimum, since edge records are duplicated per endpoint for rapid traversal.
4. Avoid wide attribute types (e.g. huge text blocks) on hot vertices. Store heavy text or metadata in secondary stores or compress them.

## Common mistakes
- Modeling every relational table column as a new vertex. This results in massive graph size and excessive traversals. Use vertex attributes for simple lookup fields.
- Using undirected edges everywhere, which increases memory footprint and makes query pruning harder.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
