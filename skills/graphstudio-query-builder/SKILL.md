---
name: graphstudio-query-builder
description: >
  Write, compile, and execute GSQL queries in GraphStudio's GSQL Editor. Use when writing queries with syntax highlights and run visuals.
license: MIT
---
# Visual Query Writing & GSQL Editor

## When to use this
Use when writing queries with immediate syntax feedback, compiling them, and visualizing the output graph directly in the browser.

## Prerequisites
Published graph schema. Links:
- [GraphStudio Design Docs](https://docs.tigergraph.com/graphstudio/current/intro/)

## Steps
1. Click **Write Queries** in GraphStudio.
2. Click the **Create Query** button (plus sign) and input a query name.
3. Use the GSQL editor to write query logic.
4. Click the **Save & Compile** button to install the query on the engine.
5. Click the **Run** button, fill in parameter variables, and run query.

## Common mistakes
- Expecting the query to execute after clicking Save. You must click the **Compile/Install** button to run query outputs in GraphStudio.
- Printing massive JSON payloads that lag the browser tab; limit output size when viewing visually.

## Sources
- [https://docs.tigergraph.com/graphstudio/current/intro/](https://docs.tigergraph.com/graphstudio/current/intro/)
