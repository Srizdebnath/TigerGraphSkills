---
name: savanna-connect-graphstudio
description: >
  Connect to TigerGraph Savanna using the visual GraphStudio web interface. Use when designing schemas, loading data visually, or exploring graphs visually.
license: MIT
---
# Connecting to Savanna with GraphStudio

## When to use this
Use when a user wants to access the graphical design tools of TigerGraph Savanna to visualize, map, and query their graph database.

## Prerequisites
An active Savanna workspace in the 'Active' status. Links:
- [TigerGraph Savanna Workspace Portal](https://savanna.tigergraph.com)

## Steps
1. Log in to the TigerGraph Savanna console.
2. Locate the active workspace you want to connect to.
3. Click on the **GraphStudio** button/link next to the workspace.
4. GraphStudio will open in a new tab, automatically authenticating you using your Savanna session credentials.
5. Select or create a graph in the top-left dropdown to start modeling.

## Common mistakes
- Trying to open GraphStudio on a workspace that is in the 'Stopped' or 'Paused' state. You must start the workspace first.
- Accessing via public URL without correct credentials if using standard self-managed. On Savanna, authentication is handled via Single Sign-On from the console.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
