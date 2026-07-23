---
name: security-key-rotation
description: >
  Rotate SSL/TLS certificates, API secrets, and user passwords. Use when executing periodic database security updates.
license: MIT
---
# Rotating Secrets & Credentials

## When to use this
Use when security policies mandate credential rotation, or when secrets are compromised and need immediate replacement.

## Prerequisites
Admin permissions. Links:
- [TigerGraph Security Documentation](https://docs.tigergraph.com)

## Steps
1. Rotate user passwords via GSQL:
   ```gsql
   ALTER USER app_reader SET PASSWORD "new_password"
   ```
2. Generate new API secrets in the cloud console or via CLI, and update all client application configs before deleting old secrets.
3. Replace SSL certificate files and run `gadmin restart nginx -y` to load updated certificates.

## Common mistakes
- Deleting old secrets before verifying that all client applications have successfully updated to the new credentials, causing immediate API downtime.
- Forgetting to restart nginx or web servers after updating SSL certificate files.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
