---
name: gsql-loading-upsert-rules
description: >
  Understand and configure vertex and edge upsert/merge logic during data loads. Use when custom merging values or appending arrays.
license: MIT
---
# Configuring Vertex and Edge Upsert Rules

## When to use this
Use when importing data that needs to merge with existing records, such as accumulative attributes, list appending, or ignoring specific updates.

## Prerequisites
Basic understanding of data loading. Links:
- [GSQL Loading Job Reference](https://docs.tigergraph.com)

## Steps
1. By default, TigerGraph updates existing vertex attributes with the latest loaded row value (upsert).
2. Customize loading behaviors to add numerical values using the `+` operator mapping:
   ```gsql
   # Add loaded count to existing count attribute
   LOAD file1 TO VERTEX User VALUES ($0, $1, User.score + $2);
   ```
3. Use conditional load clauses (`WHERE`) to only update rows under specific criteria:
   ```gsql
   LOAD file1 TO VERTEX User VALUES ($0, $1, $2) WHERE $3 == "active";
   ```

## Common mistakes
- Expecting composite keys to automatically map when names differ; all components of the primary key must align perfectly.
- Performing massive math mappings directly in loader jobs instead of handling transform logic in pre-processing stages.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
