---
name: ai-ml-workbench
description: >
  Configure TigerGraph ML Workbench for graph neural networks. Use when training PyTorch Geometric or DGL GNN models.
license: MIT
---
# Integrating TigerGraph ML Workbench

## When to use this
Use when training machine learning models on graphs to predict nodes, classify transactions, or predict missing edges.

## Prerequisites
TigerGraph ML Workbench environment installed. Links:
- [TigerGraph Self-managed Docs](https://docs.tigergraph.com)

## Steps
1. Log in to the TigerGraph ML Workbench notebook environment.
2. Configure the connection to your active TigerGraph instance.
3. Select your ML task (e.g. Node Classification) and fetch data batches using pyTigerGraph GDS loaders.
4. Train your GNN model (e.g., GCN, GAT) in Jupyter notebooks.
5. Save the trained node embeddings back to the TigerGraph database vertex attributes.

## Common mistakes
- Training models on active transactional nodes without caching datasets, causing system lag. Train on copy backups or replicas.
- Mismatched PyTorch version configurations in container images.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
