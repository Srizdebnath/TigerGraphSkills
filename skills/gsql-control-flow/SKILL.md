---
name: gsql-control-flow
description: >
  Implement loops and conditional control structures (IF, WHILE, FOREACH) inside GSQL queries. Use when building iterative algorithms.
license: MIT
---
# GSQL Control Flow & Loops

## When to use this
Use when writing path-finding algorithms (e.g. Breadth-First Search) or convergence-based calculations (e.g. PageRank) that require loops.

## Prerequisites
GSQL query logic understanding. Links:
- [GSQL Query Statements](https://docs.tigergraph.com)

## Steps
1. Write conditional blocks inside your query body:
   ```gsql
   IF target_user == "" THEN
       PRINT "Invalid user";
   END;
   ```
2. Implement iterative loops using the `WHILE` statement (e.g. traversing until no new vertices are visited):
   ```gsql
   WHILE ActiveSet.size() > 0 LIMIT 10 DO
       ActiveSet = SELECT t FROM ActiveSet:s - (friend) - User:t
                   WHERE t.@visited == FALSE
                   ACCUM t.@visited += TRUE;
   END;
   ```
3. Iterate over collection structures using `FOREACH`.

## Common mistakes
- Running infinite loops. Always include a safety `LIMIT` clause in your `WHILE` loops (e.g., `LIMIT 100`) to prevent runaway queries.
- Changing vertex sets inside a `FOREACH` iteration dynamically without using accumulator sets.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
