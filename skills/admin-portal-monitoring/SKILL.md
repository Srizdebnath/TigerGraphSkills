---
name: admin-portal-monitoring
description: >
  Monitor system resources, CPU, RAM, and active requests in the TigerGraph Admin Portal. Use when checking status and cluster load.
license: MIT
---
# System Monitoring via Admin Portal

## When to use this
Use when checking service health, investigating slow queries, checking memory usages, or auditing active cluster network traffic.

## Prerequisites
Access to Admin Portal (port 14240 or via Cloud Console). Links:
- [Admin Portal Documentation](https://docs.tigergraph.com)

## Steps
1. Log in to the TigerGraph Admin Portal.
2. Open the **Dashboard** page to view live CPU, RAM, and disk utilization graphs.
3. Click the **Service Status** tab to verify if components like GSE, GPE, or REST++ are active.
4. Open the **Active Queries** panel to monitor running queries and abort stuck or high-memory tasks.

## Common mistakes
- Ignoring RAM usage alarms. If memory approaches GSE limits, optimize queries or upgrade compute nodes before OOM occurs.
- Forgetting that metrics reflect all nodes in a distributed environment.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
