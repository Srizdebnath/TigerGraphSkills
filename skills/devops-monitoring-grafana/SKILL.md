---
name: devops-monitoring-grafana
description: >
  Configure TigerGraph monitoring using the official Grafana integration. Use when setting up system alert dashboards.
license: MIT
---
# Monitoring with Grafana & Prometheus

## When to use this
Use when monitoring cluster performance metrics (disk, memory, network, queries/sec) visually using Prometheus and Grafana dashboards.

## Prerequisites
Installed Prometheus and Grafana instances. Links:
- [TigerGraph Grafana Repo](https://github.com/tigergraph/grafana)

## Steps
1. Enable Prometheus metric exporter in TigerGraph config:
   ```bash
   gadmin config set System.PrometheusExporter.Enable true
   gadmin config apply -y
   gadmin restart -y
   ```
2. Configure Prometheus to scrape metrics from the TigerGraph exporter port (usually port 9100 or 9166).
3. Import the official TigerGraph dashboards into your Grafana instance.
4. Set up alerts on critical metrics like memory utilization and service down status.

## Common mistakes
- Leaving Prometheus exporter metrics open to public traffic. Secure metrics ports behind firewalls.
- Scraping metrics at too high frequency (e.g. every 1 second), which can put minor resource overhead on thin compute nodes.

## Sources
- [https://github.com/tigergraph/grafana](https://github.com/tigergraph/grafana)
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
