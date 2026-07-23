---
name: rest-error-handling
description: >
  Understand, decode, and handle REST++ API error responses. Use when diagnosing failing API requests and HTTP statuses.
license: MIT
---
# Interpreting REST++ Error Codes

## When to use this
Use when debug routing REST++ API calls that return non-200 HTTP statuses or return error code fields.

## Prerequisites
Completed REST++ HTTP request. Links:
- [REST++ Reference](https://docs.tigergraph.com)

## Steps
1. Inspect the HTTP status code (e.g. 400 Bad Request, 401 Unauthorized, 500 Server Error).
2. Examine the JSON response body which contains detailed code descriptors:
   ```json
   {
     "error": true,
     "code": "REST-1002",
     "message": "Graph name not found"
   }
   ```
3. Match common error codes: `REST-1000` (Authentication failed), `REST-1002` (Graph not found), `REST-3001` (Query timeout).

## Common mistakes
- Retrying failed requests infinitely on 401 Unauthorized errors without refreshing the token first.
- Parsing error codes purely based on HTTP status codes; always inspect the nested JSON payload code description.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
