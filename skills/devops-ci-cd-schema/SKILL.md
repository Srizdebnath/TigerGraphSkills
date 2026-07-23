---
name: devops-ci-cd-schema
description: >
  Build CI/CD pipelines to deploy and update graph schemas automatically. Use when automating DevOps database deploys.
license: MIT
---
# CI/CD for Graph Schema Migrations

## When to use this
Use when integrating graph database changes into agile deployment pipelines (GitHub Actions, GitLab CI/CD).

## Prerequisites
GSQL CLI access or REST API, CI/CD runner. Links:
- [GSQL Command Reference](https://docs.tigergraph.com)

## Steps
1. Save your graph DDL schemas and schema change jobs as `.gsql` files in your git repository.
2. Write a CI/CD runner script that connects to the target TigerGraph server using GSQL client or REST APIs.
3. In the runner pipeline, execute schema tests against test containers, and then apply changes using: 
   ```bash
   gsql -u $USER -p $PASS -f schema_changes.gsql
   ```

## Common mistakes
- Running destructive schema updates directly on production instances without testing on a staging environment first.
- Storing plain-text database credentials in repository script files; use CI/CD secrets variables.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
