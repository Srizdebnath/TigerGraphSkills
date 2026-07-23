---
name: gsql-schema-change
description: >
  Perform online schema changes (add/drop vertices, edges, or attributes) using GSQL Schema Change Jobs. Use when modifying existing graph databases.
license: MIT
---
# Modifying Graph Schema Online

## When to use this
Use when you need to add a new vertex type, drop an edge type, or add a new attribute to an existing vertex/edge in an active production database.

## Prerequisites
An existing graph schema. Read-Write workspace active. Links:
- [GSQL Schema Change Guide](https://docs.tigergraph.com)

## Steps
1. Create a schema change job:
   ```gsql
   USE GRAPH Social_Network
   CREATE SCHEMA_CHANGE JOB change_social {
       ADD VERTEX Company (PRIMARY_ID cid STRING, name STRING);
       ADD EDGE works_at (FROM User, TO Company, role STRING);
       ALTER VERTEX User ADD ATTRIBUTE (email STRING);
   }
   ```
2. Run the schema change job:
   ```gsql
   RUN SCHEMA_CHANGE JOB change_social
   ```
3. Verify the changes using the `ls` command in the GSQL client.

## Common mistakes
- Trying to run schema changes without specifying the graph name (`USE GRAPH`). Schema changes are specific to a target graph.
- Dropping attributes that are currently referenced by active, installed GSQL queries. This will cause compilation errors or query execution failures.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
