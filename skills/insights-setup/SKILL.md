---
name: insights-setup
description: >
  Configure and install TigerGraph Insights for dashboarding. Use when enabling no-code business intelligence visualization screens.
license: MIT
---
# Setting up TigerGraph Insights

## When to use this
Use when building business dashboards, operational visualization views, or sharing graph metrics with non-technical stakeholders.

## Prerequisites
TigerGraph Savanna or self-managed environment with Insights support. Links:
- [TigerGraph Insights Docs](https://docs.tigergraph.com)

## Steps
1. Enable the Insights component in your cluster configuration.
2. Open the TigerGraph portal and click on **Insights** (or open port 14240/insights).
3. Establish connection to your active graph schema.
4. Create your first empty dashboard workspace.

## Common mistakes
- Trying to deploy Insights on legacy TigerGraph 2.x/3.x versions that lack Insights support.
- Running Insights analytics on active transactional databases without calculating load impacts.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
