---
name: gsql-perf-secondary-indexes
description: >
  Configure secondary indexes on vertex and edge attributes in TigerGraph. Use when accelerating attribute-based query lookups.
license: MIT
---
# Creating and Using Secondary Indexes

## When to use this
Use when queries frequently perform lookups or filtering on non-key attributes (e.g., searching users by email or transactions by country).

## Prerequisites
An existing graph schema. Links:
- [GSQL Indexing Docs](https://docs.tigergraph.com)

## Steps
1. Define a secondary index using GSQL DDL inside a schema change job:
   ```gsql
   USE GRAPH Social_Network
   CREATE SCHEMA_CHANGE JOB add_idx {
       ALTER VERTEX User ADD INDEX user_email_idx ON (email);
   }
   RUN SCHEMA_CHANGE JOB add_idx
   ```
2. The engine will build the index in the background.
3. Query filters on indexed attributes will now automatically use index-level lookups instead of scanning all vertex instances.

## Common mistakes
- Creating indexes on attributes with extremely high cardinality or very low uniqueness unless needed for exact matches.
- Adding indexes to every single attribute. Each index increases memory footprint and slightly slows down data loading speeds.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
