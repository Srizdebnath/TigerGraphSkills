---
name: gsql-loading-db-jdbc
description: >
  Load database records from relational engines (Postgres, MySQL, Oracle) using GSQL JDBC drivers. Use when syncing standard DB tables.
license: MIT
---
# Ingesting Data via JDBC/Relational DBs

## When to use this
Use when loading tabular records from a standard SQL database directly into TigerGraph via JDBC connection configurations.

## Prerequisites
JDBC driver jar file for the source database. Links:
- [JDBC Loading Reference](https://docs.tigergraph.com)

## Steps
1. Define a loading job with JDBC configuration parameters:
   ```gsql
   CREATE LOADING JOB load_jdbc FOR GRAPH Social_Network {
       DEFINE FILENAME f = "jdbc_config.json";
       LOAD f TO VERTEX User VALUES ($0, $1, $2);
   }
   ```
2. Create `jdbc_config.json` containing credentials and the SQL query:
   ```json
   {
       "driver": "org.postgresql.Driver",
       "url": "jdbc:postgresql://localhost:5432/mydb",
       "username": "dbuser",
       "password": "dbpass",
       "query": "SELECT id, name, age FROM users"
   }
   ```
3. Execute the load:
   ```gsql
   RUN LOADING JOB load_jdbc USING f="jdbc_config.json"
   ```

## Common mistakes
- Forgetting to place the appropriate JDBC driver JAR in the TigerGraph server's lib directory.
- Running open-ended SQL select statements that lock tables on production transaction databases. Always use limited queries or read replicas.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
