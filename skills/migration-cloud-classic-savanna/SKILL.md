---
name: migration-cloud-classic-savanna
description: >
  Migrate database graphs from Cloud Classic to TigerGraph Savanna. Use when migrating cloud instances and schema objects.
license: MIT
---
# Migrating to TigerGraph Savanna

## When to use this
Use when migrating databases, schemas, or query repositories from the legacy TigerGraph Cloud Classic to the new Savanna environment.

## Prerequisites
Access to both legacy Cloud Classic and new Savanna console. Links:
- [Savanna Overview Documentation](https://docs.tigergraph.com/savanna/main/overview/overview)

## Steps
1. In Cloud Classic, run the export schema command to save GSQL DDL statements:
   ```bash
   gsql "EXPORT SCHEMA" > classic_schema.gsql
   ```
2. Export the database data files or download backup snapshots from the Cloud Classic console.
3. Create a new Read-Write workspace in TigerGraph Savanna.
4. Log in to Savanna Web Shell, apply the GSQL schema scripts, and configure data imports via S3/Snowflake loaders to reload records.

## Common mistakes
- Expecting direct snapshot restorations between Cloud Classic (single-tenant architecture) and Savanna (cloud-native storage/compute separated architecture). You must recreate schema structure and reload data files.
- Attempting to run legacy gadmin configuration scripts directly on Savanna workspaces.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
