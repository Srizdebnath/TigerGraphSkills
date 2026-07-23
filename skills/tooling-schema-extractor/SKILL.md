---
name: tooling-schema-extractor
description: >
  Extract active GSQL schemas using Python or shell extraction scripts. Use when auditing schema structures dynamically.
license: MIT
---
# Using the GSQL Schema Extractor

## When to use this
Use when scripting automated database auditing, documenting schemas, or translating models to documentation.

## Prerequisites
Access to GSQL CLI or python driver. Links:
- [TigerGraph Schema Extraction Docs](https://github.com/tigergraph/ecosys/blob/master/docs/awesome.md)

## Steps
1. Execute the GSQL client schema export tool command or run pyTigerGraph schema readers.
2. Run a python script to parse the returned JSON schema definitions: 
   ```python
   schema = conn.getSchema(force=True)
   # Parse vertices and edges list
   ```
3. Export parsed outputs as markdown or JSON schema files.

## Common mistakes
- Over-parsing raw strings when pyTigerGraph provides pre-formatted JSON structures.

## Sources
- [https://github.com/tigergraph/ecosys/blob/master/docs/awesome.md](https://github.com/tigergraph/ecosys/blob/master/docs/awesome.md)
