---
name: security-multitenancy
description: >
  Implement multi-tenancy and data isolation techniques. Use when partitioning schemas and separating client databases.
license: MIT
---
# Designing Multi-Tenant Graph Architectures

## When to use this
Use when building SaaS applications where multiple clients share the same graph database but cannot access each other's data.

## Prerequisites
Basic schema design and Multi-Graph knowledge. Links:
- [TigerGraph Security Documentation](https://docs.tigergraph.com)

## Steps
1. **Logical Isolation (Multi-Graph)**: Create separate graphs per tenant, assigning users permissions strictly to their target graph.
2. **Physical Isolation**: Deploy separate compute nodes or instances per client (for high security).
3. **Attribute-Based Isolation**: Add a `tenant_id` attribute to vertices/edges, and enforce filter clauses `WHERE tenant_id == current_tenant` in all queries.

## Common mistakes
- Depending purely on client-side software filtering for isolation. Database-level boundaries (separate graphs or users) are required to prevent data leakage.
- Sharing cache or global accumulators across tenants.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
