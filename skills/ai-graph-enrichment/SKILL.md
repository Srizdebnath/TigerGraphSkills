---
name: ai-graph-enrichment
description: >
  Extract entities and relationships from raw text documents using LLMs and load them into TigerGraph. Use when building knowledge graphs.
license: MIT
---
# Graph Enrichment using LLMs

## When to use this
Use when structuring unstructured PDF manuals, emails, or reports into clean nodes and connections inside a TigerGraph database.

## Prerequisites
LLM text processing pipeline, TigerGraph write token. Links:
- [TigerGraph GraphRAG Repo](https://github.com/tigergraph/graphrag)

## Steps
1. Segment raw text documents into chunks.
2. Pass text chunks to LLM, prompting it to output entities (e.g. organization, person) and relations in JSON format matching your schema.
3. Parse LLM output in your Python pipeline.
4. Write the parsed JSON list of nodes and edges directly to TigerGraph using pyTigerGraph dataframes.

## Common mistakes
- Over-generating duplicate vertices with slightly different names (e.g. 'IBM' vs 'International Business Machines'). Use entity resolution techniques during ingestion.
- Writing text chunks to the database without tracking document source origins.

## Sources
- [https://github.com/tigergraph/graphrag](https://github.com/tigergraph/graphrag)
