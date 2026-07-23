---
name: ai-llm-query-generation
description: >
  Generate GSQL queries safely using LLMs. Use when configuring AI agents that translate natural language queries to database GSQL.
license: MIT
---
# LLM-Assisted GSQL Query Generation

## When to use this
Use when building Natural Language to GSQL (NL2GSQL) agents that generate and execute GSQL queries dynamically from user questions.

## Token-Efficient Schema Prompting Technique

Dumping complete DDL schema statements into LLM system prompts wastes thousands of tokens. Use compact graph signature notation to reduce prompt token consumption by **up to 85%**:

```text
# Token-Heavy DDL Format (~450 tokens):
CREATE VERTEX User (PRIMARY_ID id STRING, name STRING, age INT, email STRING, created_at DATETIME) WITH stats="OUTDEGREE_BY_EDGETYPE";
CREATE DIRECTED EDGE friend (FROM User, TO User, since DATETIME) WITH REVERSE_EDGE="friend_of";

# Token-Efficient Compact Notation (~60 tokens):
Vertices: User(id, name, age)
Edges: User -[friend]-> User
```

## Prerequisites
- Access to TigerGraph schema via pyTigerGraph.
- LLM provider (OpenAI, Anthropic, Gemini, etc.).
- Reference: [TigerGraph GraphRAG Repository](https://github.com/tigergraph/graphrag)

## Steps
1. **Extract Compact Schema**: Convert your database schema into compact notation (`Vertex(attr1, attr2)` and `Source -[Edge]-> Target`).
2. **Construct System Prompt**: Pass the compact schema along with GSQL accumulator syntax rules (`SumAccum`, `@local`, `@@global`) to the LLM.
3. **Generate GSQL Query**: Request the LLM to output a `CREATE QUERY` block or `INTERPRET QUERY` block.
4. **Safety & Security Validation**: Scan the generated GSQL code for forbidden DDL keywords (`DROP`, `DELETE`, `ALTER`, `CREATE SCHEMA_CHANGE`) before execution.
5. **Execute Interpreted Query**: Run the query safely via `conn.runInterpretedQuery(...)` using a read-only token.

## Common mistakes
- **Unvalidated Execution**: Running raw LLM-generated code without checking for data-modifying DDL commands.
- **SQL Syntax Fallback**: Not providing the LLM with GSQL accumulator syntax examples, causing it to hallucinate standard relational SQL `GROUP BY` syntax instead of `ACCUM` / `POST-ACCUM`.

## Sources
- [https://github.com/tigergraph/graphrag](https://github.com/tigergraph/graphrag)
- [https://docs.tigergraph.com](https://docs.tigergraph.com)

