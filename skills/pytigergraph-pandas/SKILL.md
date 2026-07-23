---
name: pytigergraph-pandas
description: >
  Load Pandas DataFrames to TigerGraph and export query results back to Pandas. Use when connecting Python data workflows.
license: MIT
---
# Pandas Data Ingestion & Extraction

## When to use this
Use when importing processed dataframes from Jupyter notebooks, or loading database queries directly into pandas for analytics.

## Prerequisites
Pandas package installed. Links:
- [pyTigerGraph Intro](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. Bulk load a Pandas DataFrame into a vertex type:
   ```python
   import pandas as pd
   
   df = pd.DataFrame([{"id": "U1", "name": "Alice", "age": 25}])
   conn.upsertVertexDataFrame(
       df=df,
       vertexType="User",
       v_id="id",
       attributes={"name": "name", "age": "age"}
   )
   ```
2. Extract query results directly into a DataFrame:
   ```python
   df_results = conn.getVertexDataframe("User")
   ```

## Common mistakes
- Trying to load millions of rows in a single DataFrame call without configuring chunking, which can cause local or remote memory exhaustion. Use batch sizes of 10k-50k.
- Mismatched column names between pandas and vertex properties.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
