---
name: security-single-sign-on
description: >
  Configure LDAP/Active Directory SSO for TigerGraph interfaces. Use when integrating enterprise authentication networks.
license: MIT
---
# Configuring LDAP and Single Sign-On

## When to use this
Use when corporate policies mandate central user management and SSO for GraphStudio and Admin Portal logins.

## Prerequisites
LDAP server address, bind DN, and domain configuration details. Links:
- [TigerGraph Security Documentation](https://docs.tigergraph.com)

## Steps
1. Configure LDAP details using `gadmin` parameters:
   ```bash
   gadmin config set Security.LDAP.Enable true
   gadmin config set Security.LDAP.Host "ldap.mycompany.com"
   gadmin config set Security.LDAP.Port 389
   gadmin config set Security.LDAP.BindDN "cn=admin,dc=mycompany,dc=com"
   ```
2. Save and apply configurations:
   ```bash
   gadmin config apply -y
   gadmin restart gsql -y
   ```

## Common mistakes
- Not testing authentication connection locally using tools like `ldapsearch` before enabling configuration in TigerGraph, making it hard to identify authentication errors.
- Mismatched user attributes mappings (e.g. mapping `uid` instead of `sAMAccountName` in AD environments).

## Sources
- [https://docs.tigergraph.com](https://docs.tigergraph.com)
