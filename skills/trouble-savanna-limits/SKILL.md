---
name: trouble-savanna-limits
description: >
  Manage and work around TigerGraph Savanna compute and storage quotas. Use when hitting workspace performance limits.
license: MIT
---
# Understanding Savanna Limits & Quotas

## When to use this
Use when experiencing workspace auto-pauses, storage full warnings, or hitting limits on active graphs inside Savanna.

## Prerequisites
Savanna workspace account. Links:
- [Savanna FAQs](https://docs.tigergraph.com/savanna/main/resources/faqs)

## Steps
1. Monitor workspace consumption metrics on the Savanna Management Console.
2. Note storage thresholds; if consumption reaches 90%, prune unnecessary tables, delete expired logs, or upgrade storage capacity.
3. Adjust auto-pause settings to keep workspaces online during heavy API testing periods.
4. Avoid creating too many active graphs on small tier instances.

## Common mistakes
- Ignoring auto-pause rules, which pause compute nodes after 1 hour of inactivity. Ensure client applications can handle temporary pauses and trigger restarts.
- Storing raw uncompressed CSV payloads inside server directories.

## Sources
- [https://docs.tigergraph.com/savanna/main/resources/faqs](https://docs.tigergraph.com/savanna/main/resources/faqs)
