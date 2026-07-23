---
name: savanna-free-tier
description: >
  Manage and understand TigerGraph Savanna Free Tier constraints and migration to paid. Use when verifying storage, compute, and pause rules on the free tier.
license: MIT
---
# Understanding Savanna Free Tier Limits

## When to use this
Use when a user has questions about Savanna Free Tier resources, auto-pause schedules, or how to upgrade their workspace to a paid tier.

## Prerequisites
A TigerGraph Savanna account. Links:
- [TigerGraph Savanna Portal](https://savanna.tigergraph.com)

## Steps
1. Log in to Savanna console.
2. Note that the Free Tier allows 1 active workspace with limited RAM (typically 2GB) and storage (typically 20GB).
3. To prevent auto-pause (occurs after 1 hour of inactivity), keep active queries running or upgrade the workspace.
4. To upgrade, navigate to **Billing**, add a payment method, select your workspace, and click **Upgrade**.

## Common mistakes
- Forgetting that the free tier workspace auto-pauses after 1 hour of inactivity. If your application loses connection, check if the workspace needs to be restarted in the console.
- Expecting high-performance parallel processing on free tier hardware, which is intended only for development and sandbox testing.

## Sources
- [https://docs.tigergraph.com/savanna/main/resources/faqs](https://docs.tigergraph.com/savanna/main/resources/faqs)
