---
name: security-encryption
description: >
  Configure SSL/TLS in-transit and encryption at-rest in TigerGraph. Use when configuring security certificates and cluster compliance.
license: MIT
---
# Configuring SSL/TLS & Encryption

## When to use this
Use when securing TigerGraph network endpoints, encrypting communications between cluster nodes, or setting up production compliance.

## Prerequisites
Root access, valid SSL certificate and key files. Links:
- [TigerGraph Security Documentation](https://docs.tigergraph.com)

## Steps
1. Copy your SSL certificate and key files to the server.
2. Enable HTTPS via `gadmin` configuration commands:
   ```bash
   gadmin config set REST++.BasicConfig.EnableSSL true
   gadmin config set REST++.BasicConfig.SSLCert /path/to/cert.pem
   gadmin config set REST++.BasicConfig.SSLKey /path/to/key.pem
   ```
3. Apply configs and restart services:
   ```bash
   gadmin config apply -y
   gadmin restart nginx restpp -y
   ```

## Common mistakes
- Using expired certs, which instantly breaks all pyTigerGraph or web client connections.
- Forgetting to open the SSL port (defaults to 443 on Savanna, 9000 for HTTPS REST++ if configured) in firewall configurations.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
