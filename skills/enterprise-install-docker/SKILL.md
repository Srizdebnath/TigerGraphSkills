---
name: enterprise-install-docker
description: >
  Install and configure TigerGraph Enterprise edition using Docker containers. Use when spinning up local development environments or test containers on-premise.
license: MIT
---
# Installing TigerGraph Enterprise via Docker

## When to use this
Use when a user wants a quick, local installation of self-managed TigerGraph without installing OS packages directly.

## Prerequisites
Docker installed and running. At least 4 cores and 8GB RAM allocated to Docker. Links:
- [TigerGraph Docker Hub](https://hub.docker.com/r/tigergraph/tigergraph-developer)
- [TigerGraph Self-managed Docs](https://docs.tigergraph.com)

## Steps
1. Pull the official TigerGraph developer image:
   ```bash
   docker pull tigergraph/tigergraph-developer:latest
   ```
2. Run the container, mapping the appropriate ports (14240 for GraphStudio, 9000 for REST++, 22 for SSH):
   ```bash
   docker run -d -p 14240:14240 -p 9000:9000 -p 2222:22 --name tigergraph-sandbox --ulimit nofile=65536:65536 tigergraph/tigergraph-developer:latest
   ```
3. Wait about 1-2 minutes for the system services to initialize.
4. Access GraphStudio in your browser at `http://localhost:14240`.

## Common mistakes
- Not setting the `ulimit` for file descriptors (`nofile=65536:65536`). TigerGraph requires a large number of open file descriptors and will fail to start without it.
- Restricting RAM in Docker settings. If Docker is limited to 2GB, services like the GSQL server or REST++ will crash continuously.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
