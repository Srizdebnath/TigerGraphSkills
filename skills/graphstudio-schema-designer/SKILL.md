---
name: graphstudio-schema-designer
description: >
  Design graph schemas visually using TigerGraph GraphStudio. Use when drawing vertices, edges, attributes, and keys in a web interface.
license: MIT
---
# Visual Schema Design with GraphStudio

## When to use this
Use when visual developers or analysts want to build or update a TigerGraph schema using GraphStudio graphical tools.

## Prerequisites
Access to active workspace and GraphStudio. Links:
- [GraphStudio Design Docs](https://docs.tigergraph.com/graphstudio/current/intro/)

## Steps
1. Open GraphStudio and click **Design Schema** in the left menu.
2. Click the **Add Vertex** button, click on canvas, and fill in vertex name and attributes.
3. Click the **Add Edge** button, click on the source vertex, then target vertex, and configure directed/undirected options.
4. Click **Publish Schema** in the top toolbar to apply changes to the database.

## Common mistakes
- Forgetting to click the **Publish Schema** button. Changes made on the canvas are local browser drafts until published.
- Trying to rename existing vertices/edges visually on published databases without understanding that data drops might occur.

## Sources
- [https://docs.tigergraph.com/graphstudio/current/intro/](https://docs.tigergraph.com/graphstudio/current/intro/)
