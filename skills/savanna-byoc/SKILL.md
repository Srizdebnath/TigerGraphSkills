---
name: savanna-byoc
description: >
  Overview of Bring Your Own Cloud (BYOC) setup for TigerGraph Savanna. Use when planning to deploy Savanna compute resources inside your own AWS/Azure/GCP VPC.
license: MIT
---
# Bring Your Own Cloud (BYOC) Setup Overview

## When to use this
Use when a corporate user requests guidance on running TigerGraph Savanna while keeping the data within their own enterprise cloud infrastructure.

## Prerequisites
Enterprise tier TigerGraph Savanna agreement and cloud admin rights. Links:
- [TigerGraph Savanna BYOC Support](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. Contact TigerGraph sales/support to enable the BYOC feature on your account.
2. Configure IAM roles and policies in your cloud account (e.g., AWS IAM Role) to grant TigerGraph control plane permission to spin up resources.
3. Input your Cloud Account ID and Role ARN in the Savanna Console under Cloud Accounts.
4. Launch a workspace, choosing your customized private VPC/subnet configuration.

## Common mistakes
- Restricting IAM role permissions too heavily, which causes workspace deployment failures. Ensure the role conforms exactly to the JSON policy provided by TigerGraph.
- Assuming BYOC is available on the free tier. This is strictly an enterprise plan feature.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
