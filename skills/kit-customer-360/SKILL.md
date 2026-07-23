---
name: kit-customer-360
description: >
  Deploy and customize the Customer 360 Solution Kit. Use when unifying client touchpoints and mapping product journeys.
license: MIT
---
# Adapting Customer 360 Solution Kit

## When to use this
Use when mapping user interactions across websites, support portals, purchases, and marketing lists to construct a complete timeline.

## Prerequisites
TigerGraph workspace. Links:
- [TigerGraph Solutions Overview](https://www.tigergraph.com/ecosystem/)

## Steps
1. Initialize the Customer 360 solution kit.
2. Ingest customer profiles, order history, website clickstream logs, and support ticket records.
3. Run the path queries to map interactions in chronological order.
4. Adapt visualization dashboards to display timelines and key metrics for individual customer views.

## Common mistakes
- Attempting to load uncompressed streaming raw log files directly, causing database overload. Filter and parse logs beforehand.
- Creating schemas with excessive hops to lookup details. Store static metadata directly on vertices.

## Sources
- [https://www.tigergraph.com/ecosystem/](https://www.tigergraph.com/ecosystem/)
