---
name: ai-graphrag-setup
description: >
  Install and configure TigerGraph GraphRAG repository. Use when building LLM search engines with graph context retrieval.
license: MIT
---
# Setting up TigerGraph GraphRAG

## When to use this
Use when establishing GraphRAG applications that query TigerGraph schemas to provide structured context to LLMs (OpenAI, Anthropic).

## Prerequisites
Python environment, LLM API keys. Links:
- [TigerGraph GraphRAG Repo](https://github.com/tigergraph/graphrag)

## Steps
1. Clone the official TigerGraph GraphRAG repository:
   ```bash
   git clone https://github.com/tigergraph/graphrag.git
   cd graphrag
   ```
2. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure connection details inside the `.env` configuration file, listing host, secret, and LLM endpoint configs.
4. Run the demo application script to verify LLM connection.

## Common mistakes
- Hallucinating schema definitions. Ensure the GraphRAG configuration file lists the exact graph schemas and vertex attributes, otherwise the query builder will fail.
- Using public keys in code; load keys via environment variables.

## Sources
- [https://github.com/tigergraph/graphrag](https://github.com/tigergraph/graphrag)
