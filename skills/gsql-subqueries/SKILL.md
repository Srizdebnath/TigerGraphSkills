---
name: gsql-subqueries
description: >
  Implement and run GSQL subqueries and user-defined functions inside queries. Use when modularizing complex traversal logic.
license: MIT
---
# Writing GSQL Subqueries

## When to use this
Use when query operations contain repetitive sub-traversals that should be structured as clean, callable functions.

## Prerequisites
Advanced GSQL query skills. Links:
- [GSQL Subquery Reference](https://docs.tigergraph.com)

## Steps
1. Define a subquery with the `CREATE QUERY` syntax, specifying query returns:
   ```gsql
   CREATE QUERY get_friend_count(VERTEX<User> u) RETURNS INT FOR GRAPH Social_Network {
       Start = {u};
       Result = SELECT t FROM Start:s - (friend) - User:t;
       RETURN Result.size();
   }
   ```
2. Call the subquery within your main query execution block:
   ```gsql
   CREATE QUERY main_query() FOR GRAPH Social_Network {
       Start = {User.*};
       Result = SELECT s FROM Start:s
                POST-ACCUM s.friend_count = get_friend_count(s);
   }
   ```

## Common mistakes
- Calling heavy subqueries inside an `ACCUM` clause. Subqueries inside `ACCUM` execute per-edge, which can devastate performance. Run them in `POST-ACCUM` or as sequential hops instead.
- Expecting nested subqueries to access global accumulators of the parent query automatically.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
