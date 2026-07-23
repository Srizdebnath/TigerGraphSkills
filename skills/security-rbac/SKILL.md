---
name: security-rbac
description: >
  Configure Role-Based Access Control (RBAC) in TigerGraph. Use when creating roles, granting permissions, and restricting graph objects.
license: MIT
---
# Configuring Role-Based Access Control

## When to use this
Use when configuring database-level users, securing schema changes, or granting minimal execution privileges to api users.

## Prerequisites
Admin credentials on TigerGraph Enterprise. Links:
- [TigerGraph Security Documentation](https://docs.tigergraph.com)

## Steps
1. Create a custom database user:
   ```gsql
   CREATE USER app_reader "reader_password"
   ```
2. Grant standard roles to the user on a specific graph:
   ```gsql
   GRANT ROLE queryreader TO app_reader ON GRAPH Social_Network
   ```
3. For custom scopes, create custom roles and bind permissions:
   ```gsql
   CREATE ROLE schema_editor
   GRANT ALTER SCHEMA ON GRAPH Social_Network TO schema_editor
   GRANT ROLE schema_editor TO app_reader
   ```

## Common mistakes
- Assigning the `superuser` role to web API servers. Superuser can modify system configs and drop databases. Use `queryreader` or `querywriter` instead.
- Forgetting that GSQL user names are case-sensitive.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
