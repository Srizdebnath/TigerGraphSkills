---
name: enterprise-install-kubernetes
description: >
  Deploy TigerGraph Enterprise in Kubernetes using the official TigerGraph Operator. Use when setting up scalable, self-managed cloud or on-prem clusters.
license: MIT
---
# Installing TigerGraph via Kubernetes Operator

## When to use this
Use when configuring Kubernetes (K8s) environments for enterprise deployments requiring orchestration, high availability, and automated scaling.

## Prerequisites
Kubernetes cluster (v1.22+), kubectl, Helm installed. Links:
- [TigerGraph Kubernetes Operator Docs](https://docs.tigergraph.com)

## Steps
1. Add the TigerGraph Helm repository:
   ```bash
   helm repo add tigergraph https://tigergraph.github.io/ecosys/
   helm repo update
   ```
2. Install the TigerGraph Operator:
   ```bash
   helm install tg-operator tigergraph/tigergraph-operator --namespace tigergraph --create-namespace
   ```
3. Define a Custom Resource Definition (CRD) file `tigergraph-cluster.yaml` specifying nodes, volume sizes, and replica configurations.
4. Deploy the cluster:
   ```bash
   kubectl apply -f tigergraph-cluster.yaml
   ```
5. Monitor deployment status:
   ```bash
   kubectl get tigergraph -n tigergraph
   ```

## Common mistakes
- Allocating insufficient persistent storage to the volume templates. The database requires stable, fast (SSD) storage class mounts.
- Not configuring headless services correctly, which prevents internal nodes in a distributed TigerGraph cluster from communicating.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
- [https://github.com/tigergraph/ecosys](https://github.com/tigergraph/ecosys)
