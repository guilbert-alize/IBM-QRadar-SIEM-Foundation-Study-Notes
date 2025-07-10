# User Management and Security Profiles

## Overview
This chapter summarizes the **User Management and Security Profiles** course from the IBM QRadar SIEM Foundation learning path. It covers how IBM QRadar SIEM manages user access and data segmentation. I used **Grok**, created by xAI, to refine my notes for clarity and accuracy.

## User Management
QRadar provides granular access control for secure operations:

- **User Accounts and Roles**:
  - **Accounts**: Unique usernames with assigned roles, security profiles, and tenant settings.
  - **Roles**: Define functions (e.g., viewing dashboards, managing offenses). Default roles include Admin (full access) and All.
  - **Security Profiles**: Restrict access to networks, log sources, and domains. Admin profile grants full access; custom profiles limit visibility.

- **Authentication Methods**:
  - **Local**: Default system authentication.
  - **RADIUS/TACACS**: Encrypts usernames for terminal access.
  - **Microsoft AD/LDAP**: Integrates with enterprise directories.
  - **SAML**: Supports federated Single Sign-On (SSO).

- **Domains and Multitenancy**:
  - **Domains**: Segment data (events, flows, assets) by source to manage overlapping IPs or restrict visibility (e.g., for business units).
  - **Multitenancy**: Enables Managed Security Service Providers (MSSPs) to serve multiple clients using tenant-specific domains.
  - **Domain Tagging**: Applied in the event pipeline to associate events with domains.

## Key Takeaways
QRadar’s user management ensures secure, role-based access and data segmentation for enterprise and MSSP environments.
