---
name: algo-knn
description: >
  Install and run the k-Nearest Neighbors (kNN) classification algorithm. Use when classifying vertices based on proximity to labeled neighbors.
license: MIT
---
# Running k-Nearest Neighbors (kNN)

## When to use this
Use when predicting the category or class of unlabeled vertices based on similarity scores to nearby labeled vertices.

## Prerequisites
TigerGraph GSQL Algorithm Library installed. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Compile the kNN classification query.
2. Execute the query passing the target vertex and labels:
   ```gsql
   RUN QUERY tg_knn_classification(source_vertex="User1", v_type="User", e_type="friend", label_attr="category", k=5, print_accum=TRUE, file_path="")
   ```
3. The algorithm evaluates the top k nearest neighbors and assigns the majority label.

## Common mistakes
- Selecting an even value for k when classifying binary groups, which can lead to tie votes. Use odd numbers for k.
- Not handling cases where the source vertex has fewer than k neighbors total.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
