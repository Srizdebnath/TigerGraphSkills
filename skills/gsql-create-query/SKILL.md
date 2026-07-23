---
name: gsql-create-query
description: >
  Write, compile, and run GSQL queries. Use when writing basic traversals, parameterizing inputs, and returning graph responses.
license: MIT
---
# Creating and Running GSQL Queries

## When to use this
Use when writing custom queries in GSQL, installing them to the engine, and testing performance with interpreted mode.

## Prerequisites
Active graph schema. Links:
- [GSQL Query Reference](https://docs.tigergraph.com)

## Steps
1. Write query in a file or the shell:
   ```gsql
   CREATE QUERY get_user(STRING target_user) FOR GRAPH Social_Network {
       Start = {User.*};
       Result = SELECT s FROM Start:s WHERE s.username == target_user;
       PRINT Result;
   }
   ```
2. Run in interpreted mode (fast, no compilation lag, good for testing):
   ```gsql
   INTERPRET QUERY get_user("john_doe")
   ```
3. Compile and install the query for production execution:
   ```gsql
   INSTALL QUERY get_user
   ```
4. Execute the installed query:
   ```gsql
   RUN QUERY get_user("john_doe")
   ```

## Common mistakes
- Installing queries after every minor code edit. Installation takes 30-60 seconds. Use `INTERPRET QUERY` during development instead.
- Forgetting `FOR GRAPH` in query signature, which is required for non-schema-free GSQL queries.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
