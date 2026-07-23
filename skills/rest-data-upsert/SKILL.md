---
name: rest-data-upsert
description: >
  Insert or update vertex and edge data using REST++ POST requests. Use when performing real-time transaction writes.
license: MIT
---
# Upserting Data via REST++

## When to use this
Use when writing single records or small batches of transactional updates directly to TigerGraph without a loading job.

## Prerequisites
Graph schema defined. Links:
- [REST++ Ingest Guide](https://docs.tigergraph.com)

## Steps
1. Format your write payload in JSON format:
   ```json
   {
     "vertices": {
       "User": {
         "User3": {
           "name": {"value": "Charlie"},
           "age": {"value": 28}
         }
       }
     }
   }
   ```
2. Send a POST request to the payload endpoint:
   ```bash
   curl -X POST -H "Authorization: Bearer MY_TOKEN" \
     -d @payload.json "http://localhost:9000/graph/Social_Network"
   ```

## Common mistakes
- Using this endpoint for bulk loads (e.g. millions of rows). The transactional POST endpoint is optimized for speed on small transactions; use GSQL Loading Jobs for high-throughput imports.
- Confusing vertex attributes format; ensure values are nested under property names properly.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
