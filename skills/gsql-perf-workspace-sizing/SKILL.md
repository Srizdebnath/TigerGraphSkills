---
name: gsql-perf-workspace-sizing
description: >
  Select correct TigerGraph workspace specifications based on workload profiles. Use when configuring Savanna sizing plans.
license: MIT
---
# Sizing Savanna Workspaces for OLTP/OLAP

## When to use this
Use during system design to determine CPU, memory, and sharding needs for transactional (OLTP) vs. analytical (OLAP) requirements.

## Prerequisites
TigerGraph Savanna architecture understanding. Links:
- [Savanna Workspace Docs](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. For OLTP (high concurrent lookups, minor traversals): size instances with high CPU core counts and low-latency storage. Set up multiple replica workspaces.
2. For OLAP (heavy graph algorithms, machine learning): prioritize RAM size. Scale up memory capacity to fit all vertices, edges, and intermediate accumulator states.
3. Assess your graph footprint: estimate `(Number of Vertices * Vertex Size) + (Number of Edges * Edge Size * 2)` to calculate base memory requirement.
4. Allocate at least 2.5x base memory size to cover query runtime accumulator state.

## Common mistakes
- Sizing based purely on disk database sizes. Graphs run in memory; if your in-memory footprint exceeds RAM size, the database will crash or thrash swap memory.
- Using a single workspace for both high-throughput live APIs (OLTP) and massive deep-hop reporting queries (OLAP). Separate them into read-write and read-only workspaces.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
- [https://docs.tigergraph.com/savanna/main/resources/faqs](https://docs.tigergraph.com/savanna/main/resources/faqs)
