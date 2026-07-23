---
name: insights-dashboard-design
description: >
  Design dashboards with interactive filters, global variables, and page link triggers. Use when building client dashboards.
license: MIT
---
# Designing Interactive Dashboards

## When to use this
Use when creating multi-widget dashboards that let users input search terms, filter dates, and explore connections dynamically.

## Prerequisites
Insights setup and target widgets configured. Links:
- [TigerGraph Insights Docs](https://docs.tigergraph.com)

## Steps
1. Add a **Filter Control** widget to the top of your dashboard.
2. Bind the filter control to a global parameter (e.g., `start_date` or `user_id`).
3. Configure downstream query widgets to accept these global variables as query inputs.
4. Organize widgets in grids, and apply styling templates.
5. Test inputs to verify dashboard refresh rates.

## Common mistakes
- Hardcoding values in query widgets instead of routing them to interactive controls.
- Overcrowding a single page with too many network visualizations, which can lag client browsers.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
