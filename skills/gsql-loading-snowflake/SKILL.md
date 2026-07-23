---
name: gsql-loading-snowflake
description: >
  Ingest data from Snowflake warehouses using the Snowflake connector. Use when importing clean structured warehouse tables into graph.
license: MIT
---
# Loading Data from Snowflake

## When to use this
Use when connecting a Snowflake data platform directly to TigerGraph to sync records into vertices and edges.

## Prerequisites
Snowflake account, database, warehouse, schema, role, and credentials. Links:
- [Snowflake Loader Documentation](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. Create a configuration file containing your Snowflake credentials and query details.
2. Define a loading job referencing the Snowflake datasource connection:
   ```gsql
   CREATE LOADING JOB load_snowflake FOR GRAPH Social_Network {
       DEFINE FILENAME f = "snowflake_config.json";
       LOAD f TO VERTEX User VALUES ($0, $1, $2);
   }
   ```
3. Execute the loading job:
   ```gsql
   RUN LOADING JOB load_snowflake USING f="snowflake_config.json"
   ```

## Common mistakes
- Exporting extremely large tables from Snowflake without filter clauses, leading to memory issues. Filter or paginate data on the Snowflake side.
- Hardcoding connection passwords inside configuration files stored in code repositories.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
