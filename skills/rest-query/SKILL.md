---
name: rest-query
description: >
  Run installed GSQL queries by sending REST++ requests. Use when fetching query results over standard HTTP endpoints.
license: MIT
---
# Invoking Queries via REST++

## When to use this
Use when integrating TigerGraph analytical results into web applications, reporting dashboards, or microservices.

## Prerequisites
An installed GSQL query. Links:
- [REST++ Query Reference](https://docs.tigergraph.com)

## Steps
1. Send a GET request to the query endpoint, passing arguments as URL query parameters:
   ```bash
   curl -X GET -H "Authorization: Bearer MY_TOKEN" \
     "http://localhost:9000/query/Social_Network/find_connections?target_user=User1&cities=New+York"
   ```
2. Note the URL path format: `/query/<graph_name>/<query_name>`.
3. Check the returned JSON structure containing your printed variables.

## Common mistakes
- Omitting the `Authorization` header when REST++ authentication is enabled, resulting in connection rejection.
- URL-encoding parameters incorrectly, particularly for lists or special characters.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
