---
name: savanna-create-workspace
description: >
  Create and configure a workspace in TigerGraph Savanna. Use when deploying a new compute instance, choosing regions, or selecting instance types on Savanna.
license: MIT
---
# Creating a Savanna Workspace

## When to use this
Use when a user needs to launch a new database workspace (compute node) in TigerGraph Savanna, select regions, or choose between Read-Write and Read-Only workspaces.

## Prerequisites
An active TigerGraph Savanna account with sufficient permissions. Links:
- [TigerGraph Savanna Workspace Portal](https://savanna.tigergraph.com)
- [Savanna Workspace Docs](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. Log in to the TigerGraph Savanna console.
2. Click on **Workspaces** in the left navigation panel.
3. Click **Create Workspace**.
4. Enter a workspace name, select a cloud provider (AWS), select the target region, and select the instance size (e.g., Free, TG.S1.micro, etc.).
5. Select the workspace type: **Read-Write** (for schema changes and data ingestion) or **Read-Only** (for read-intensive queries).
6. Click **Create** and wait for the workspace status to change to **Active**.

## Common mistakes
- Trying to run schema modifications or loading jobs on a **Read-Only (RO)** workspace. Schema changes and loading jobs must be run on a **Read-Write (RW)** workspace.
- Leaving idle workspaces active. Always stop or delete unused workspaces to avoid running up charges (though free tier has auto-pause).

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
- [https://docs.tigergraph.com/savanna/main/resources/faqs](https://docs.tigergraph.com/savanna/main/resources/faqs)
