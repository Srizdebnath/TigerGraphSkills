---
name: gsql-loading-spark
description: >
  Configure the TigerGraph Spark Connector to load large datasets from Spark DataFrames. Use when managing large-scale distributed ETL pipelines.
license: MIT
---
# Ingesting Data using Apache Spark

## When to use this
Use when your data processing occurs on a Spark cluster (Hadoop, Databricks) and you need to push computed data directly to TigerGraph.

## Prerequisites
Running Spark cluster and the TigerGraph Spark Connector jar. Links:
- [Spark Connector GitHub](https://github.com/tigergraph/ecosys)

## Steps
1. Add the TigerGraph Spark Connector dependency to your Spark environment.
2. Write your Spark application (Scala/Python/Java) to load data into a DataFrame.
3. Write the DataFrame to TigerGraph using the connector format:
   ```python
   df.write \
     .format("com.tigergraph.spark") \
     .option("host", "http://127.0.0.1") \
     .option("graph", "Social_Network") \
     .option("username", "tigergraph") \
     .option("password", "tigergraph") \
     .option("vertex", "User") \
     .save()
   ```

## Common mistakes
- Overloading the TigerGraph database with too many concurrent Spark partitions. Limit parallelism using Spark repartitioning if TigerGraph is saturated.
- Mismatched schema data types between the Spark DataFrame columns and the GSQL vertex/edge properties.

## Sources
- [https://github.com/tigergraph/ecosys](https://github.com/tigergraph/ecosys)
