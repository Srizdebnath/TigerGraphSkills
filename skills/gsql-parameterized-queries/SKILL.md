---
name: gsql-parameterized-queries
description: >
  Write GSQL queries that accept external parameters (vertex sets, datetimes, lists, primitives). Use when creating APIs.
license: MIT
---
# Parameterized Queries in GSQL

## When to use this
Use when exposing queries to external REST applications or Python drivers that need to pass run-time variables and filters.

## Prerequisites
GSQL create query basics. Links:
- [GSQL Query Parameter Reference](https://docs.tigergraph.com)

## Steps
1. Declare parameter variables in the query signature:
   ```gsql
   CREATE QUERY find_connections(VERTEX<User> target_user, DATETIME min_date, LIST<STRING> cities) FOR GRAPH Social_Network {
       Start = {target_user};
       Result = SELECT t FROM Start:s - (friend) - User:t
                WHERE t.join_date > min_date AND t.city IN cities;
       PRINT Result;
   }
   ```
2. Run the query, passing parameters via the command line or REST request.

## Common mistakes
- Not sanitizing input strings inside client applications before passing them to parameters, though GSQL protects against SQL injection natively.
- Mismatched datetime formats. Ensure client applications serialize dates to standard string formats compatible with GSQL datetime conversion.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
