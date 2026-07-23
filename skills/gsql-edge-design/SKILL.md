---
name: gsql-edge-design
description: >
  Design and define edge types using GSQL DDL. Use when defining directed, undirected, or directed edges with reverse edge counterparts.
license: MIT
---
# Designing GSQL Edges

## When to use this
Use when defining the relationships (edges) between vertices in your graph schema, specifying flow direction, and configuring attributes on edges.

## Prerequisites
Existing vertex definitions in the schema. Links:
- [GSQL Edge DDL Guide](https://docs.tigergraph.com)

## Steps
1. Open the GSQL editor.
2. For undirected relationships (bidirectional), use `CREATE UNDIRECTED EDGE`:
   ```gsql
   CREATE UNDIRECTED EDGE friend (FROM User, TO User, connect_time DATETIME);
   ```
3. For directed relationships, use `CREATE DIRECTED EDGE`:
   ```gsql
   CREATE DIRECTED EDGE purchase (FROM User, TO Product, price DOUBLE, purchase_time DATETIME);
   ```
4. To enable backward traversal on directed edges efficiently, define a reverse edge name:
   ```gsql
   CREATE DIRECTED EDGE purchase (FROM User, TO Product, price DOUBLE) WITH REVERSE_EDGE="purchased_by";
   ```

## Common mistakes
- Defining two separate directed edges instead of using `WITH REVERSE_EDGE`. The reverse edge mechanism is much more memory-efficient and automatically managed by TigerGraph.
- Placing unnecessary attributes on edges, which significantly increases memory footprint compared to vertex attributes.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
