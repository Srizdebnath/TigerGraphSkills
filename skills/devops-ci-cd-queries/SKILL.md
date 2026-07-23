---
name: devops-ci-cd-queries
description: >
  Configure CI/CD pipelines to build, compile, and test GSQL queries automatically. Use when deploying code to staging/production.
license: MIT
---
# CI/CD for GSQL Query Deployments

## When to use this
Use when developers check query edits into Git, requiring automatic testing, compilation, and query deployment on clusters.

## Prerequisites
Git repo, CI/CD runner setup. Links:
- [GSQL Command Reference](https://docs.tigergraph.com)

## Steps
1. Store your GSQL query codes as `.gsql` files in version control.
2. Configure pipeline to run linting checks on queries using GSQL compiler locally in test containers.
3. Execute compile and installation commands programmatically:
   ```bash
   gsql -u $USER -p $PASS "INSTALL QUERY get_user_data"
   ```
4. Execute post-install API tests to verify endpoints return valid data.

## Common mistakes
- Over-compiling queries. Compiling queries takes time (30-60s each). Only compile/install queries that have changed.
- Not running query validation tests inside pipelines.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
