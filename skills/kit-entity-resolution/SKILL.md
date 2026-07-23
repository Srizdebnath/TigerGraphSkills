---
name: kit-entity-resolution
description: >
  Configure the Entity Resolution Solution Kit. Use when merging duplicate records, matching customers, and connecting nodes.
license: MIT
---
# Adapting the Entity Resolution Kit

## When to use this
Use when unifying multiple customer profiles, merging duplicate identities, or deduplicating account records across database files.

## Prerequisites
TigerGraph environment. Links:
- [TigerGraph Solutions Overview](https://www.tigergraph.com/ecosystem/)

## Steps
1. Import the Entity Resolution kit schema which models relationships like `same_as` or `matches`.
2. Ingest identity feeds containing names, emails, phone numbers, and addresses.
3. Execute the provided match queries which analyze edit distance, common attributes, and shared connections.
4. Generate weighted score links and establish `same_as` edges between duplicate records.

## Common mistakes
- Merging nodes physically instead of logically using edges. In graphs, it is best practice to link records using a `same_as` edge so audit trails are preserved, rather than deleting records.
- Not establishing thresholds for match confidence, leading to massive over-linking.

## Sources
- [https://www.tigergraph.com/ecosystem/](https://www.tigergraph.com/ecosystem/)
