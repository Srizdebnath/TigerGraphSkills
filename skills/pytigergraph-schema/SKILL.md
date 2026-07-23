---
name: pytigergraph-schema
description: >
  Inspect, define, and modify graph schemas from Python using pyTigerGraph. Use when automating database setup scripts.
license: MIT
---
# Managing Schemas via pyTigerGraph

## When to use this
Use when programmatically validating existing schema structures or deploying schema updates within Python CI/CD pipelines.

## Prerequisites
Active connection with admin privileges. Links:
- [pyTigerGraph Intro](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. Fetch the database schema structure:
   ```python
   schema = conn.getSchema(force=True)
   print(schema)
   ```
2. Access details about vertex and edge types from the returned dictionary.
3. Send custom GSQL DDL commands to modify schemas programmatically:
   ```python
   conn.gsql('''
   USE GRAPH Social_Network
   CREATE SCHEMA_CHANGE JOB add_attr {
       ALTER VERTEX User ADD ATTRIBUTE (new_score INT);
   }
   RUN SCHEMA_CHANGE JOB add_attr
   ''')
   ```

## Common mistakes
- Calling `getSchema()` frequently in tight loops. Cache the output locally to prevent duplicate network calls.
- Running schema modifications on read-only compute nodes.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
