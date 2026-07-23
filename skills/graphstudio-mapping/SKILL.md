---
name: graphstudio-mapping
description: >
  Map CSV/data files to vertices and edges visually in GraphStudio. Use when aligning tabular columns to graph property attributes.
license: MIT
---
# Visual Data Mapping in GraphStudio

## When to use this
Use when configuring mapping pipelines visually in GraphStudio instead of writing manual loading jobs.

## Prerequisites
Graph schema published, data files uploaded. Links:
- [GraphStudio Design Docs](https://docs.tigergraph.com/graphstudio/current/intro/)

## Steps
1. Click **Map Data To Design** in GraphStudio.
2. Add data files to the workspace by uploading local CSVs.
3. Click the **Add Data Mapping** line connecting a file to a vertex or edge type.
4. Drag columns from the file preview card to the matching attributes on the schema card.
5. Save the configuration.

## Common mistakes
- Not mapping all parts of a composite primary key. The loader will fail if key fields are unmapped.
- Forgetting to handle date format conversions in the mapping property window.

## Sources
- [https://docs.tigergraph.com/graphstudio/current/intro/](https://docs.tigergraph.com/graphstudio/current/intro/)
