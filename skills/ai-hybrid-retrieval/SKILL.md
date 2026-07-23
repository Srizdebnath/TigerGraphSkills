---
name: ai-hybrid-retrieval
description: >
  Combine vector similarity search with GSQL multi-hop graph traversal. Use when building high-accuracy GraphRAG pipelines.
license: MIT
---
# Implementing Hybrid Search Retrieval (GraphRAG)

## When to use this
Use when AI search engines need to find matching items via vector embeddings (semantic search) and then traverse relationships in GSQL to retrieve precise context.

## Efficiency Comparison: GSQL + GraphRAG vs. Normal SQL & Vector RAG

| Metric / Dimension | Standard Vector RAG (LLM Context Stuffing) | Relational SQL + RAG | GSQL + GraphRAG (TigerGraph) |
| :--- | :--- | :--- | :--- |
| **Token Consumption** | High (10k–50k+ tokens per query via chunk dumping) | High to Medium | **Low (80%–95% token reduction)** by sending minimal structured subgraphs |
| **Query Complexity** | N/A (no relationship traversal) | Exponential $O(R^N)$ with multi-table `JOIN`s | **Linear $O(V + E)$** parallel vertex traversals |
| **Multi-Hop Latency** | High (fails to capture indirect connections) | 100ms–10s+ (multi-JOIN bottleneck) | **<10ms–50ms** across millions of nodes |
| **Hallucination Rate** | High (unstructured text context ambiguity) | Medium | **Near Zero** (deterministic graph path grounding) |

## Prerequisites
- Target graph schema loaded in TigerGraph (Local Docker or Savanna Cloud).
- Embeddings stored on vertex attributes or integrated vector index.
- Reference: [TigerGraph GraphRAG Repository](https://github.com/tigergraph/graphrag)

## Steps
1. **Vector Seed Search**: Retrieve top-K seed vertices using vector similarity search on vertex embedding attributes.
2. **GSQL Multi-Hop Context Retrieval**: Pass seed vertex IDs to a compiled GSQL query that traverses relationships (e.g. 2-hop neighborhood) and accumulates structured facts.
   ```gsql
   CREATE QUERY get_graph_context(SET<VERTEX<User>> seeds) FOR GRAPH Social_Network {
       SumAccum<STRING> @facts;
       
       Start = {seeds};
       # Hop 1: Get direct connections
       Hop1 = SELECT t FROM Start:s - (friend:e) - User:t
              ACCUM s.@facts += (s.name + " is friend of " + t.name + ".\n");
              
       # Return compact, token-efficient string representation
       PRINT Start[Start.name, Start.@facts];
   }
   ```
3. **Token-Efficient Prompt Formatting**: Compress the extracted GSQL subgraph into concise line statements (e.g. `Alice -> friend -> Bob`) instead of raw JSON dumps before passing to the LLM prompt context.

## Common mistakes
- **Raw JSON Context Stuffing**: Passing unformatted JSON dumps of entire graph nodes to the LLM. Always extract short, line-based triple statements (`Subject -> Predicate -> Object`) to maximize prompt token efficiency.
- **Unbounded Graph Hops**: Running 3+ hop traversals without limiting result sets, leading to combinatorial node explosion and memory limits.

## Sources
- [https://github.com/tigergraph/graphrag](https://github.com/tigergraph/graphrag)
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)

