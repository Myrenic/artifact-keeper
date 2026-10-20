---
section: Added
issues: [#4297]
---
- **Admins can pre-provision OIDC-managed groups before the first user login** (#4297). `POST /api/v1/admin/sso/oidc/{provider_id}/groups` with `{"name": "..."}` creates the group in that provider's namespace (or returns the existing one), so projects and permissions can reference it before anyone in it has signed in; a later login whose group claim names it joins the same group. This enables declarative and IaC-driven RBAC configuration while keeping the IdP authoritative for membership; the new admin API reuses the existing ownership-safe federated-group provisioning path and does not create users or memberships.
