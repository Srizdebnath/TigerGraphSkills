---
name: savanna-api-keys
description: >
  Generate, manage, and rotate API keys and secrets in TigerGraph Savanna. Use when configuring programmatic authentication for APIs, pyTigerGraph, or REST++.
license: MIT
---
# Managing API Keys in TigerGraph Savanna

## When to use this
Use when a user needs to obtain credentials to connect to a TigerGraph Savanna workspace from Python, REST clients, or external ETL services.

## Prerequisites
Access to an active TigerGraph Savanna workspace. Links:
- [TigerGraph Savanna Console](https://savanna.tigergraph.com)

## Steps
1. Log in to the TigerGraph Savanna console.
2. Navigate to your workspace detail page.
3. Locate the **Access Management** or **API Keys** section.
4. Click **Generate API Key** or **Create Secret**.
5. Copy the generated Key and Secret immediately; for security reasons, the secret will not be displayed again.
6. Store the credentials securely (e.g., in a `.env` file or secret manager).

## Common mistakes
- Committing the API secret key to public Git repositories. Always use environment variables.
- Confusing the workspace API key with database-level users/passwords. Savanna API keys are specifically for cloud-level authentication.

## Sources
- [https://docs.tigergraph.com/savanna/main/resources/faqs](https://docs.tigergraph.com/savanna/main/resources/faqs)
