---
name: rest-auth
description: >
  Request, validate, and manage authorization tokens for TigerGraph REST++ endpoints. Use when building secure API integrations.
license: MIT
---
# REST++ Authentication & Token Management

## When to use this
Use when making direct HTTP/REST calls to a TigerGraph cluster from custom programming languages or API tools like Postman.

## Prerequisites
REST++ port reachable (usually 9000 or 443). Links:
- [REST++ Auth Documentation](https://docs.tigergraph.com)

## Steps
1. Request an authorization token by sending a POST request to the `/requesttoken` endpoint:
   ```bash
   curl -X POST -d '{"secret":"MY_DATABASE_SECRET", "lifetime":3600}' http://localhost:9000/requesttoken
   ```
2. Parse the returned JSON to retrieve the token string.
3. Include the token in all subsequent database requests inside the Authorization header:
   ```bash
   Authorization: Bearer <your_token>
   ```

## Common mistakes
- Forgetting that tokens have an expiration lifetime. Renew tokens in client applications before they expire to avoid 401 Unauthorized errors.
- hardcoding secrets inside clients; always retrieve tokens using backend auth loops.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
