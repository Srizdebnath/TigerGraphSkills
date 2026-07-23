---
name: pytigergraph-queries
description: >
  Execute pre-installed and interpreted GSQL queries from pyTigerGraph. Use when extracting query results into Python structures.
license: MIT
---
# Running Queries with pyTigerGraph

## When to use this
Use when calling GSQL queries from analytical pipelines and processing return data as JSON structures.

## Prerequisites
Installed query in TigerGraph database. Links:
- [pyTigerGraph Intro](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. Call an installed query, passing arguments as a dictionary:
   ```python
   results = conn.runInstalledQuery(
       "find_connections", 
       params={"target_user": "User1", "cities": ["New York", "Boston"]}
   )
   print(results)
   ```
2. For temporary queries, use interpreted execution (slower execution but no compilation delay):
   ```python
   results = conn.runInterpretedQuery(
       "INTERPRET QUERY () FOR GRAPH Social_Network { Start = {User.*}; PRINT Start.size(); }"
   )
   ```

## Common mistakes
- Passing incorrect parameter types (e.g. passing integer values as strings to numeric parameters), which triggers REST API errors.
- Running extremely large queries that exceed REST++ response body limits. Page results or save to files instead.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
