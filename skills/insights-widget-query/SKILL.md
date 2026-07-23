---
name: insights-widget-query
description: >
  Bind GSQL query outputs to table, chart, and graph widgets in TigerGraph Insights. Use when configuring interactive charts.
license: MIT
---
# Binding GSQL Queries to Insights Widgets

## When to use this
Use when you need to drive dashboards using custom GSQL queries that return metrics, lists, or paths.

## Prerequisites
Installed GSQL query that prints compatible JSON formats. Links:
- [TigerGraph Insights Docs](https://docs.tigergraph.com)

## Steps
1. In Insights, open your dashboard and click **Add Widget**.
2. Select widget type (e.g. Bar Chart, Pie Chart, Network Graph).
3. Under data source, select **GSQL Query** and pick your installed query from the dropdown.
4. Map query output JSON fields to widget coordinates, labels, or sizes.
5. Click **Preview** and save widget.

## Common mistakes
- Writing GSQL queries for widgets that return deeply nested, custom-structured JSON. Insights requires flat array tables or standard node/edge lists to bind widgets.
- Returning thousands of records to simple bar charts, which slows down dashboard rendering.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
