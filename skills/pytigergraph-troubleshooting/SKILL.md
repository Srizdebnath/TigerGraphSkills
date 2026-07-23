---
name: pytigergraph-troubleshooting
description: >
  Debug connection errors, certificate issues, and timeout failures in pyTigerGraph. Use when python scripts fail to connect.
license: MIT
---
# Troubleshooting pyTigerGraph Connections

## When to use this
Use when encountering connection refused, invalid tokens, ssl certificate verification failures, or REST++ timeouts.

## Prerequisites
Python script attempting to connect. Links:
- [pyTigerGraph Diagnostics](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. If certificate verification fails, and you are using a self-signed dev certificate, disable verification explicitly (dev only):
   ```python
   conn = TigerGraphConnection(host="...", verifyRequest=False)
   ```
2. Verify the target restpp port is reachable (9000 by default for standard, 443 for Savanna TLS).
3. Check if your API token has expired and generate a new one using the database secret.
4. Enable verbose logging to see raw HTTP headers.

## Common mistakes
- Disabling request verification (`verifyRequest=False`) in production environments, creating MITM security vulnerabilities.
- Confusing database authentication password with the GSQL secret key.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
