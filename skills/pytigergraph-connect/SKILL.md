---
name: pytigergraph-connect
description: >
  Install, configure, and establish a secure connection using the pyTigerGraph driver. Use when building Python applications.
license: MIT
---
# Connecting with pyTigerGraph (Local Docker & Cloud)

## When to use this
Use when establishing Python driver connections (`pyTigerGraph`) to a TigerGraph instance running either locally in Docker or hosted on TigerGraph Cloud (Savanna / TGCloud).

## Connection Configurations: Local Docker vs. Cloud-Based

### Option A: Connecting to Local Docker Instance
When running TigerGraph locally inside a Docker container (`tigergraph/tigergraph-developer`):
```python
from pyTigerGraph import TigerGraphConnection

# Connect to Local Docker instance
conn = TigerGraphConnection(
    host="http://localhost",        # Local host address
    restppPort=9000,                # REST++ port
    gsPort=14240,                   # GraphStudio / GSQL port
    graphname="Social_Network",
    username="tigergraph",          # Default developer credentials
    password="tigergraph",
    tgCloud=False                   # Set to False for local/on-prem
)

# Authenticate if secret/token is enabled
# conn.getToken(secret="YOUR_LOCAL_SECRET")

print(conn.echo())
```

### Option B: Connecting to Cloud-Based Instance (Savanna / TGCloud)
When connecting to a managed cloud instance:
```python
from pyTigerGraph import TigerGraphConnection

# Connect to TGCloud / Savanna Instance
conn = TigerGraphConnection(
    host="https://my-workspace.savanna.tigergraph.com", # Full workspace HTTPS URL
    graphname="Social_Network",
    username="tigergraph",
    password="YOUR_SAVANNA_PASSWORD",
    tgCloud=True                    # Set to True for managed cloud
)

# Acquire session authorization token using secret key
conn.getToken(secret="YOUR_CLOUD_SECRET")

print(conn.echo())
```

## Steps
1. Install `pyTigerGraph` using pip:
   ```bash
   pip install pyTigerGraph
   ```
2. Determine your target environment (Local Docker vs Cloud-Based).
3. Initialize `TigerGraphConnection` with the correct `tgCloud`, `host`, and port parameters shown above.
4. Call `conn.echo()` to verify connection health.

## Common mistakes
- **Mismatched `tgCloud` Flag**: Setting `tgCloud=False` when connecting to Savanna or Cloud Classic. Setting `tgCloud=True` forces pyTigerGraph to route through port 443 with HTTPS, whereas `tgCloud=False` uses default ports 9000/14240.
- **Missing Token Generation**: Attempting to execute REST++ endpoints or queries on Cloud instances without calling `conn.getToken(secret=...)` after initialization.
- **Port Block in Docker**: Forgetting to map ports `9000:9000` and `14240:14240` when launching the Docker container locally.

## Sources
- [https://docs.tigergraph.com/pytigergraph/current/intro/](https://docs.tigergraph.com/pytigergraph/current/intro/)
- [https://docs.tigergraph.com/savanna/main/overview/overview](https://docs.tigergraph.com/savanna/main/overview/overview)

