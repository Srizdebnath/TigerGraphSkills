---
name: pytigergraph-gds
description: >
  Utilize Graph Data Science (GDS) loaders to export graph data directly to PyTorch Geometric (PyG) or DGL. Use when training GNN models.
license: MIT
---
# Using pyTigerGraph GDS Loaders

## When to use this
Use when pulling graph structures, vertex attributes, and relationships into Python to train Graph Neural Networks (GNNs).

## Prerequisites
PyTorch, PyTorch Geometric, or DGL installed. Links:
- [pyTigerGraph GDS Loaders](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. Import the GDS featurizer/loader tools.
2. Initialize a vertex or edge loader, specifying batch size and features:
   ```python
   loader = conn.gds.vertexLoader(
       num_batches=10,
       attributes=["age", "score"],
       v_in_db=True
   )
   for batch in loader:
       print(batch)  # Returns batches formatted for ML models
   ```

## Common mistakes
- Running GDS loaders on massive clusters without specifying neighborhood sampling limits, causing client OOM crashes.
- Mismatched PyTorch / CUDA library versions, which breaks backend ML operations.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
