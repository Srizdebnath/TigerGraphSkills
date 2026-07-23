---
name: enterprise-install-bare-metal
description: >
  Install TigerGraph Enterprise directly on Linux bare metal or Virtual Machines. Use when performing single-node or multi-node custom OS setups.
license: MIT
---
# Installing TigerGraph on Bare Metal / VMs

## When to use this
Use when installing self-managed TigerGraph on standard enterprise Linux machines (CentOS/RHEL/Ubuntu) without containerization.

## Prerequisites
Supported OS (Ubuntu 18.04+, CentOS/RHEL 7+), root/sudo access, minimum 8 cores, 16GB RAM. Links:
- [TigerGraph Installation Guide](https://docs.tigergraph.com)

## Steps
1. Download the installation tarball from the TigerGraph download portal.
2. Extract the package:
   ```bash
   tar -xzf tigergraph-<version>-enterprise.tar.gz
   cd tigergraph-<version>-enterprise
   ```
3. Run the interactive installer:
   ```bash
   sudo ./install.sh
   ```
4. Follow prompts to set installation directory, credentials, and network configuration.
5. Verify installation by running basic gadmin health check command:
   ```bash
   gadmin status
   ```

## Common mistakes
- Running the installer under a directory owned by root without granting the `tigergraph` system user write permissions.
- Disabling NTP or system clock sync. Multi-node clusters require microsecond-level synchronization and will fail to load or write if clocks drift.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
