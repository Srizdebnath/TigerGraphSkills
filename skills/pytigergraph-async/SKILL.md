---
name: pytigergraph-async
description: >
  Perform non-blocking query execution and batch loadings using AsyncTigerGraphConnection. Use when optimizing Python concurrency.
license: MIT
---
# Asynchronous Operations in pyTigerGraph

## When to use this
Use when building web services, fast pipelines, or concurrent workers that make multiple database calls without blocking.

## Prerequisites
Asyncio support in Python. Links:
- [pyTigerGraph Async Documentation](https://docs.tigergraph.com/pytigergraph/current/intro/)

## Steps
1. Import the async connection driver:
   ```python
   import asyncio
   from pyTigerGraph import AsyncTigerGraphConnection
   
   async def main():
       conn = AsyncTigerGraphConnection(host="https://my-host.savanna.tigergraph.com", graphname="Social")
       await conn.getToken(secret="MY_SECRET")
       result = await conn.runInstalledQuery("my_query")
       print(result)
   
   asyncio.run(main())
   ```

## Common mistakes
- Attempting to call synchronous methods on the `AsyncTigerGraphConnection` object without using `await`.
- Mixing thread pools with asyncio event loops inefficiently.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
