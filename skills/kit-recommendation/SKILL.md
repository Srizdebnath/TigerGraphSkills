---
name: kit-recommendation
description: >
  Configure and adapt the Product Recommendation Solution Kit. Use when building collaborative filter and path recommendation engines.
license: MIT
---
# Adapting the Recommendation Kit

## When to use this
Use when building e-commerce product recommender systems, movie recommendation services, or personalized content feeds.

## Prerequisites
TigerGraph environment. Links:
- [TigerGraph Solutions Overview](https://www.tigergraph.com/ecosystem/)

## Steps
1. Deploy the Product Recommendation kit.
2. Ingest user interaction matrices (views, purchases, ratings).
3. Deploy the pre-built collaborative filtering queries, which trace paths like `User -> purchases -> Product -> purchased_by -> User -> purchases -> Product`.
4. Calculate similarity scores and return top recommended products.
5. Fine-tune item filters to exclude already-purchased products.

## Common mistakes
- Recommending items the user has already bought because of missing filter checks.
- Running collaborative filtering on the entire active user base in real time. Cache recommendations for users offline, or calculate recommendation candidates on smaller subgraphs.

## Sources
- [https://www.tigergraph.com/ecosystem/](https://www.tigergraph.com/ecosystem/)
