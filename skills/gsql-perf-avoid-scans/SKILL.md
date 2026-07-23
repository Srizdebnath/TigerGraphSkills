---
name: gsql-perf-avoid-scans
description: >
  Design queries that start traversal from seed vertices instead of scanning the full graph. Use when optimizing query execution speeds.
license: MIT
---
# Avoiding Full-Graph Scans in GSQL

## When to use this
Use when optimizing OLTP and real-time graph queries to achieve sub-10ms response times by starting traversals from target seed vertices instead of scanning the full graph.

## Efficiency Comparison: Seeded GSQL vs. Relational SQL Scans & JOINs

| Query Pattern | Relational SQL Execution | GSQL Parallel Seed Traversal | Efficiency Advantage |
| :--- | :--- | :--- | :--- |
| **1-Hop Neighbor Lookup** | `SELECT ... JOIN ... WHERE user_id = ?` (Index Seek + Table Join) | `Start = {seed}; SELECT t FROM Start - (edge) - V:t;` | **3x–5x faster** (Direct pointer dereference) |
| **3-Hop Path Search** | 3 consecutive `JOIN` operations (requires scanning & joining temporary result tables) | 3 sequential GSQL `SELECT` steps originating from `{seed}` | **10x–100x faster** (Zero join tables created) |
| **Full Graph Scan** | `SELECT * FROM table` (Sequential disk/table read) | `Start = {User.*};` (Parallel vertex memory scan) | Parallel execution across all CPU cores |

## Prerequisites
- Familiarity with GSQL query structure.
- Reference: [TigerGraph Performance Tuning](https://docs.tigergraph.com)

## Steps
1. **Never use full-vertex start sets in OLTP APIs**: Avoid `{User.*}` in production APIs unless running global aggregations.
2. **Pass specific seed inputs**: Parameterize the query with specific vertex IDs or sets:
   ```gsql
   CREATE QUERY fast_seed_lookup(VERTEX<User> seed_user) FOR GRAPH Social_Network {
       # Initialize start set directly with seed vertex
       Start = {seed_user};
       
       # Traversal is O(Degree(seed_user)), completely independent of total graph size
       Result = SELECT t 
                FROM Start:s - (friend:e) - User:t;
       PRINT Result;
   }
   ```
3. **Use Secondary Indexes for Attribute Seeds**: If seeds are specified by property values (e.g. `email`) rather than primary IDs, create a secondary index to avoid full graph scans.

## Common mistakes
- **Scanning Millions of Vertices**: Initializing `{User.*}` when only querying a specific user's 2-hop neighborhood. This causes full-table scans and degrades performance under concurrency.
- **Missing Secondary Index**: Searching on non-primary-key attributes without defining `CREATE INDEX` on the property.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)

