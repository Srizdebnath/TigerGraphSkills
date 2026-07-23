---
name: algo-custom-udf
description: >
  Create and compile custom C++ User Defined Functions (UDFs) for TigerGraph queries. Use when adding complex math or string parsing routines.
license: MIT
---
# Compiling Custom C++ UDFs

## When to use this
Use when GSQL built-in functions are insufficient for custom cryptographic hash routines, coordinate distance logic, or high-performance math operations.

## Prerequisites
Admin access to the TigerGraph host machine (self-managed). Links:
- [TigerGraph UDF Guide](https://docs.tigergraph.com)

## Steps
1. Locate the file `ExprFunctions.hpp` on the TigerGraph host (typically under `~/.tigergraph/gstore/gstore/udf/`).
2. Add your custom C++ function definition inside the namespace code block:
   ```cpp
   inline double custom_distance(double x1, double y1, double x2, double y2) {
       return sqrt(pow(x2 - x1, 2) + pow(y2 - y1, 2));
   }
   ```
3. Compile and publish the changes to the engine:
   ```bash
   gadmin config apply -y
   gadmin restart gse -y
   ```
4. Call the function directly in GSQL queries: `double dist = custom_distance(s.x, s.y, t.x, t.y);`.

## Common mistakes
- Storing stateful, non-thread-safe C++ functions in UDFs. Because GSQL query loops execute in highly parallel threads, UDFs must be stateless and thread-safe.
- Uploading incorrect C++ syntax that fails compilation, which blocks all queries from running or compiling until the file is fixed.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
- [https://github.com/tigergraph/ecosys](https://github.com/tigergraph/ecosys)
