---
name: gsql-loading-job-csv
description: >
  Write and run GSQL Loading Jobs to import local CSV/TSV files into TigerGraph. Use when performing bulk data ingestion from file shares.
license: MIT
---
# Loading CSV Data using GSQL

## When to use this
Use when loading tabular files or bulk data from local disks, shared storage, or container directories into TigerGraph.

## Prerequisites
An existing graph schema. Links:
- [GSQL Loading Job Reference](https://docs.tigergraph.com)

## Steps
1. Define the loading job with source-to-target mappings:
   ```gsql
   USE GRAPH Social_Network
   CREATE LOADING JOB load_users_csv FOR GRAPH Social_Network {
       DEFINE FILENAME file1;
       LOAD file1 TO VERTEX User VALUES ($0, $1, $2, $3) USING SEPARATOR=",", HEADER="true", EOL="
";
       LOAD file1 TO EDGE friend VALUES ($0, $4, $5) USING SEPARATOR=",", HEADER="true", EOL="
";
   }
   ```
2. Run the loading job, specifying the path to the CSV file:
   ```gsql
   RUN LOADING JOB load_users_csv USING file1="/path/to/users.csv"
   ```
3. Check the command output for load statistics (success, failure, lines processed).

## Common mistakes
- Incorrect separator definition (e.g., using default comma for tab-separated files).
- Forgetting to handle file headers; if `HEADER="true"` is omitted, the first line of the CSV will be parsed as data, leading to format errors or invalid vertex IDs.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
