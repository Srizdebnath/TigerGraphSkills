---
name: admin-portal-user-management
description: >
  Create users, assign privileges, and manage roles in the TigerGraph Admin Portal. Use when managing visual RBAC systems.
license: MIT
---
# Visual User Management in Admin Portal

## When to use this
Use when administrators want to configure user profiles, grant access to specific graphs, or assign roles visually.

## Prerequisites
Admin credentials on TigerGraph. Links:
- [Admin Portal Documentation](https://docs.tigergraph.com)

## Steps
1. Navigate to the **User Management** section in the Admin Portal.
2. Click the **Create User** button, enter username and password.
3. Select the user and click **Assign Roles**.
4. Pick the target graph and select roles (e.g. `queryreader`, `admin`, `designer`).
5. Save configurations.

## Common mistakes
- Granting global superuser permissions to application APIs instead of minimal graph-level read/write roles.
- Leaving default credentials unchanged after system installation.

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
