---
name: rest-data-delete
description: >
  Delete specific vertex or edge instances using REST++ DELETE requests. Use when modifying live graph records.
license: MIT
---
# Deleting Graph Data via REST++

## When to use this
Use when removing individual nodes or connections from your graph dynamically from client apps.

## Prerequisites
Active connection. Links:
- [REST++ Reference](https://docs.tigergraph.com)

## Steps
1. To delete a specific vertex, send a DELETE request referencing the vertex type and ID:
   ```bash
   curl -X DELETE -H "Authorization: Bearer MY_TOKEN" \
     "http://localhost:9000/graph/Social_Network/vertices/User/User3"
   ```
2. To delete an edge, specify source, edge type, and target details in the path:
   ```bash
   curl -X DELETE -H "Authorization: Bearer MY_TOKEN" \
     "http://localhost:9000/graph/Social_Network/edges/User/User1/friend/User2"
   ```

## Common mistakes
- Forgetting that deleting a vertex automatically deletes all connected edges (cascade behavior). Ensure this matches your application logic.
- Not handling return verification status codes in the client application.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
