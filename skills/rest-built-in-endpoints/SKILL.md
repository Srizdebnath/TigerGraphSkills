---
name: rest-built-in-endpoints
description: >
  Access built-in system endpoints for statistics, system health, and status queries. Use when auditing and monitoring database health.
license: MIT
---
# Using Built-In REST++ Endpoints

## When to use this
Use when scripting automated health checks, uptime monitors, or retrieving vertex/edge counts dynamically.

## Prerequisites
Access token. Links:
- [REST++ Reference](https://docs.tigergraph.com)

## Steps
1. Retrieve vertex/edge count metrics for a graph:
   ```bash
   curl -X GET -H "Authorization: Bearer MY_TOKEN" "http://localhost:9000/graph/Social_Network/vertices?count=true"
   ```
2. Check service status using health endpoints:
   ```bash
   curl -X GET "http://localhost:9000/ready"
   ```
3. Retrieve server metrics and thread usages using system parameters.

## Common mistakes
- Polling count endpoints in high frequency. Calculating graph sizes on massive databases has performance costs; cache these results where possible.
- Exposing health check endpoints to public traffic without firewall limitations.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
