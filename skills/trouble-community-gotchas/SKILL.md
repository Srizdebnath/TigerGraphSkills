---
name: trouble-community-gotchas
description: >
  Avoid common mistakes identified by the TigerGraph community. Use when query behaviors or schema configurations act unexpectedly.
license: MIT
---
# Top Community Gotchas & Solutions

## When to use this
Use when troubleshooting obscure query behaviors, timezone conversions, or unexpected upsert rules.

## Prerequisites
Access to community discussions. Links:
- [TigerGraph Community Forum](https://community.tigergraph.com)

## Steps
1. Search the [TigerGraph Community Forum](https://community.tigergraph.com) for matching symptoms.
2. Check for common gotchas: datetime formatting mismatches (e.g. UTC vs local timezone offsets), case sensitivity in GSQL, and port routing configs in docker containers.
3. Implement community-verified solutions (e.g. using specific datetime parsing flags or network bridge settings).

## Common mistakes
- Assuming UTC datetime strings are automatically parsed. Explicitly define format structures during loading jobs to ensure timestamps parse correctly.
- Using reserved GSQL keywords (e.g. `order`, `group`, `select`) as vertex or attribute names.

## Sources
- [https://community.tigergraph.com](https://community.tigergraph.com)
