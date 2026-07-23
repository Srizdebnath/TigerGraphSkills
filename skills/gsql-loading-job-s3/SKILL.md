---
name: gsql-loading-job-s3
description: >
  Configure loading jobs to ingest data directly from AWS S3 buckets. Use when connecting cloud storage to TigerGraph Savanna or Enterprise.
license: MIT
---
# Loading Data from Amazon S3

## When to use this
Use when your raw data is hosted in S3 buckets and needs to be pulled directly into TigerGraph without downloading locally.

## Prerequisites
AWS Access Key, Secret Key, and target S3 path. Links:
- [S3 Ingestion Documentation](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. Define the loading job referencing the S3 plugin syntax:
   ```gsql
   USE GRAPH Social_Network
   CREATE LOADING JOB load_s3 FOR GRAPH Social_Network {
       DEFINE FILENAME f = "s3://my-bucket/data/users.csv";
       LOAD f TO VERTEX User VALUES ($0, $1, $2) USING SEPARATOR=",", HEADER="true";
   }
   ```
2. Run the loading job, passing the AWS credentials:
   ```gsql
   RUN LOADING JOB load_s3 USING f.aws.key="MY_ACCESS_KEY", f.aws.secret="MY_SECRET_KEY", f.aws.region="us-east-1"
   ```

## Common mistakes
- Storing AWS secrets in the loading job body itself. Always pass credential variables during execution (`RUN LOADING JOB`) to keep scripts secure.
- Not ensuring the S3 bucket is in the same cloud region as the Savanna compute node, which can incur transfer latency and data egress fees.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
