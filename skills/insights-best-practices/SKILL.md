---
name: insights-best-practices
description: >
  Best practices for designing high-performance TigerGraph Insights dashboards. Use when reducing dashboard loading speeds.
license: MIT
---
# Insights Design & Performance Optimization

## When to use this
Use when dashboards load slowly, time out, or put excessive CPU load on the TigerGraph database.

## Prerequisites
Familiarity with Insights. Links:
- [TigerGraph Insights Docs](https://docs.tigergraph.com)

## Steps
1. Use parameterized queries so widgets fetch only the data they need, rather than loading large vertex sets.
2. Set cache intervals on slow widgets to reuse query responses instead of re-running GSQL traversals on every refresh.
3. Keep network graph visualization widgets restricted to showing top-K elements to keep canvas interactions smooth.
4. Avoid placing multiple complex multi-hop queries on a single dashboard tab; divide them across sub-pages.

## Common mistakes
- Fetching the entire graph structure into a visualization widget. The browser canvas will crash if rendering more than 5,000 nodes simultaneously.
- Setting refresh rates too high (e.g., every 5 seconds) on heavy reporting dashboards.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
