---
name: savanna-connect-gsql-client
description: >
  Connect to TigerGraph Savanna using the GSQL Web Shell or the GSQL CLI client. Use when executing GSQL scripts, schema definition jobs, or admin commands.
license: MIT
---
# Connecting via the GSQL Web Shell/Client

## When to use this
Use when a user wants to run GSQL commands or run scripts directly via command line, bypassing the visual GraphStudio UI.

## Prerequisites
An active workspace. Links:
- [TigerGraph Savanna Console](https://savanna.tigergraph.com)

## Steps
1. Log in to the TigerGraph Savanna console.
2. Open your workspace and locate the **GSQL Web Shell** tab.
3. Alternatively, to use the local CLI client, download the GSQL client package from TigerGraph resources.
4. Connect using the command line:
   ```bash
   gsql -u <username> -p <password> -ip <workspace-ip-or-host>
   ```
5. Run GSQL commands interactively or execute GSQL files using the `-f` flag:
   ```bash
   gsql -u <username> -p <password> -ip <host> -f schema.gsql
   ```

## Common mistakes
- Forgetting that port 14240 (or 9000 for REST++) needs to be open in firewall configurations if connecting from an external network to a self-managed server.
- Running shell commands inside the GSQL interpreter. Execute GSQL commands only, or exit the interpreter with `quit` or `exit`.

## Sources
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)
