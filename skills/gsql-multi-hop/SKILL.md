---
name: gsql-multi-hop
description: >
  Write multi-hop graph traversals in GSQL. Use when querying deep relationships, paths, and patterns across multiple connections.
license: MIT
---
# Writing Multi-Hop Traversals

## When to use this
Use when finding indirect connections (e.g., friend of a friend, transitive dependencies, path tracing) across the database.

## Prerequisites
Core GSQL SELECT statement understanding. Links:
- [GSQL SELECT Reference](https://docs.tigergraph.com)

## Steps
1. Chain multiple `SELECT` statements together, using the output of one as the input for the next:
   ```gsql
   # Hop 1: Users to their friends
   Start = {User.*};
   Hop1 = SELECT t FROM Start:s - (friend) - User:t;
   
   # Hop 2: Friends to their employers
   Hop2 = SELECT c FROM Hop1:f - (works_at) - Company:c;
   PRINT Hop2;
   ```
2. Pass state between hops using local vertex accumulators initialized in prior steps.

## Common mistakes
- Chaining too many hops in a single interpreted session without limiting target vertex set sizes (combinatorial explosion).
- Not filtering out already-visited vertices in subsequent hops, leading to cyclic infinite traversals. Use boolean accumulators like `@visited` to track path state.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
