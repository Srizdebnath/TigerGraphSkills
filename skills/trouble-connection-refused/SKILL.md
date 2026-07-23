---
name: trouble-connection-refused
description: >
  Diagnose and fix TigerGraph connection refused and timeout issues. Use when client scripts fail to connect to database ports.
license: MIT
---
# Fixing Connection Refused Errors

## When to use this
Use when REST APIs, pyTigerGraph, or GraphStudio fail to reach database hosts with connection timeouts.

## Prerequisites
Administrative network access to server or cloud console. Links:
- [Savanna FAQs](https://docs.tigergraph.com/savanna/main/resources/faqs)

## Steps
1. Verify if the target workspace/server status is 'Active' or 'Running'.
2. Test port reachability from the client terminal:
   ```bash
   curl -I http://<host>:9000/ready
   ```
3. Verify firewall policies or security groups permit inbound traffic on port 9000 (REST++), 14240 (GraphStudio), or 443 (Savanna HTTPS).
4. Check `nginx` and `gse` status on self-managed servers using `gadmin status`.

## Common mistakes
- Assuming port 9000 is open globally on cloud workspaces. In Savanna, default connections routing is through port 443 (HTTPS) under single URLs.
- Not verifying if a local proxy or VPN blocks communication ports.

## Sources
- [https://docs.tigergraph.com/savanna/main/resources/faqs](https://docs.tigergraph.com/savanna/main/resources/faqs)
