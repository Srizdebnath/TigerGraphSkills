---
name: graphstudio-loading
description: >
  Run and monitor data loading jobs visually in GraphStudio. Use when starting imports and tracking statistics in real-time.
license: MIT
---
# Visual Data Loading & Monitoring

## When to use this
Use when executing data load jobs visually and monitoring statistics (speed, rejected records) from the web console.

## Prerequisites
Data mappings defined in GraphStudio. Links:
- [GraphStudio Design Docs](https://docs.tigergraph.com/graphstudio/current/intro/)

## Steps
1. Click **Load Data** in the GraphStudio side navigation.
2. Select the target data files to load.
3. Click the **Start Loading** (play) button.
4. Monitor loading statistics, progress bars, and graph size counters in the real-time dashboard.

## Common mistakes
- Leaving a loading job running when files contain massive errors. Pause the job, inspect logs, and fix formats if reject rate is high.
- Assuming a finished loading status means 100% success; check the reject count.

## Sources
- [https://docs.tigergraph.com/graphstudio/current/intro/](https://docs.tigergraph.com/graphstudio/current/intro/)
