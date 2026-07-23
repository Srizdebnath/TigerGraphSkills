---
name: kit-fraud-detection
description: >
  Configure and adapt the pre-built Fraud Detection Solution Kit. Use when modeling transaction paths, fraud rings, and alerts.
license: MIT
---
# Adapting the Fraud Detection Kit

## When to use this
Use when building financial anti-money laundering (AML), credit card fraud, or chargeback network mapping platforms.

## Prerequisites
TigerGraph Savanna workspace or Enterprise. Links:
- [TigerGraph Solutions Overview](https://www.tigergraph.com/ecosystem/)

## Steps
1. Deploy the Fraud Detection solution kit template from the Savanna management console.
2. Inspect the pre-configured schema containing `Account`, `Transaction`, `Device`, and `IP` vertices.
3. Map your banking/payment transaction data to the kit schema.
4. Deploy and run the built-in fraud ring search queries (e.g. finding circular money flow patterns).
5. Adapt queries to incorporate custom transaction thresholds.

## Common mistakes
- Modifying core vertex names in the kit without updating the dependent pre-installed GSQL queries, breaking the visual components.
- Expecting the kit to handle real-time fraud prevention out of the box without building REST integration loops.

## Sources
- [https://www.tigergraph.com/ecosystem/](https://www.tigergraph.com/ecosystem/)
