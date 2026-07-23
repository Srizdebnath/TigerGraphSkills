---
name: kit-mule-account
description: >
  Configure the Mule Account Detection Solution Kit. Use when tracing structured transfer chains and money routing systems.
license: MIT
---
# Adapting Mule Account Detection Kit

## When to use this
Use when searching for money mule rings, structured layering patterns, or shell company routing loops in banks.

## Prerequisites
TigerGraph instance. Links:
- [TigerGraph Solutions Overview](https://www.tigergraph.com/ecosystem/)

## Steps
1. Import the Mule Account Detection kit schema.
2. Load bank account transactions, customer KYC profiles, and branch data.
3. Execute the ring-finding queries which trace paths that return money back to source nodes or pass money through suspicious transit accounts.
4. Generate risk flags on accounts based on transit speeds (velocity check).

## Common mistakes
- Ignoring tiny transaction amounts when tracing flows; money mules often break large sums into small test payments.
- Creating undirected search parameters, which fail to preserve direction of money flow.

## Sources
- [https://www.tigergraph.com/ecosystem/](https://www.tigergraph.com/ecosystem/)
