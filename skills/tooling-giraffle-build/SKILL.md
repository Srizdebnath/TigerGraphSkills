---
name: tooling-giraffle-build
description: >
  Use Giraffle, the Gradle plugin for TigerGraph, to compile schemas, load scripts, and queries. Use when automating setups.
license: MIT
---
# Using the Giraffle Build Tool

## When to use this
Use when managing TigerGraph project assets (schemas, queries, load jobs) inside version-controlled Gradle build setups.

## Prerequisites
Java environment, Gradle installed. Links:
- [TigerGraph Giraffle Tool](https://github.com/tigergraph/ecosys/blob/master/docs/awesome.md)

## Steps
1. Add the Giraffle plugin to your `build.gradle` configuration file.
2. Configure your TigerGraph server URL and authentication credentials in the gradle properties file.
3. Execute tasks to deploy schemas and install queries:
   ```bash
   gradle gsqlDeploy
   ```
4. Execute tasks to trigger loading jobs programmatically.

## Common mistakes
- Committing clear-text passwords in `gradle.properties` files. Use environment variables or Gradle credentials store.
- Incompatible JVM versions.

## Sources
- [https://github.com/tigergraph/ecosys/blob/master/docs/awesome.md](https://github.com/tigergraph/ecosys/blob/master/docs/awesome.md)
