---
name: algo-install-library
description: >
  Install the official TigerGraph GSQL Graph Algorithm Library. Use when adding PageRank, community detection, or path-finding queries to your database.
license: MIT
---
# Installing GSQL Graph Algorithm Library

## When to use this
Use when starting a new database and needing to equip it with the standard suite of Graph Data Science (GDS) algorithms.

## Prerequisites
Access to TigerGraph server or workspace. Links:
- [TigerGraph Graph Algorithms](https://github.com/tigergraph/gsql-graph-algorithms)

## Steps
1. Clone the algorithm repository:
   ```bash
   git clone https://github.com/tigergraph/gsql-graph-algorithms.git
   cd gsql-graph-algorithms
   ```
2. Run the install script, pointing to your database instance:
   ```bash
   ./install.sh -g Social_Network -u tigergraph -p tigergraph -ip localhost
   ```
3. Alternatively, open GraphStudio and choose **Install Algorithms** from the visual schema interface to load them automatically.

## Common mistakes
- Attempting to run installation scripts without verifying the GSQL compiler version matches (e.g., mismatch between 3.x and 4.x libraries).
- Installing all 50+ algorithms at once on a small sandbox instance, which can exhaust memory during parallel GSQL compilation.

## Sources
- [https://github.com/tigergraph/gsql-graph-algorithms](https://github.com/tigergraph/gsql-graph-algorithms)
