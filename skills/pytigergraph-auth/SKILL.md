---
name: pytigergraph-auth
description: >
  Manage token auth, token generation, and secret rotation in pyTigerGraph. Use when configuring secure programmatic logins.
license: MIT
---
# Authentication in pyTigerGraph

## When to use this
Use when implementing production applications that authenticate securely via tokens rather than plain-text passwords.

## Prerequisites
Existing database secret generated from GraphStudio or CLI. Links:
- [pyTigerGraph Intro](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. Initialize the connection object using host details.
2. Request a session token using the database secret:
   ```python
   token = conn.getToken(secret="MY_DATABASE_SECRET")
   # The token is saved in the connection object automatically
   ```
3. Use the token for all subsequent reads/writes, ensuring no passwords are saved in code.

## Common mistakes
- Committing the database secret key directly to version control. Load secrets from environment variables using `os.getenv("TG_SECRET")`.
- Expecting a token to last forever. Monitor token expiry times and renew/regenerate them periodically.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
