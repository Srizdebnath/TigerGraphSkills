---
name: gsql-perf-batching
description: >
  Implement batching techniques in GSQL queries. Use when processing massive graph datasets without exhausting system memory.
license: MIT
---
# Batching Query Processing

## When to use this
Use when migrating, processing, or updating millions of records in a single query run where memory footprint must be capped.

## Prerequisites
Advanced GSQL loop and accumulator understanding. Links:
- [GSQL Performance Tuning](https://docs.tigergraph.com)

## Steps
1. Define pagination or chunking filters using vertex primary key offsets or ranges.
2. Iterate through batches using a loop inside GSQL:
   ```gsql
   CREATE QUERY batch_process(INT batch_size) FOR GRAPH Social_Network {
       INT offset = 0;
       WHILE TRUE DO
           # Retrieve batch of vertices
           Batch = SELECT s FROM User:s
                   LIMIT offset, batch_size;
           IF Batch.size() == 0 THEN BREAK; END;
           # Perform updates
           Batch = SELECT s FROM Batch:s
                   POST-ACCUM s.status = "processed";
           offset = offset + batch_size;
       END;
   }
   ```

## Common mistakes
- Setting batch sizes too large (e.g. 10M+). Choose a balanced size (typically 10,000 to 100,000) depending on vertex attribute widths.
- Forgetting the break condition inside the loop, leading to infinite execution loops.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
