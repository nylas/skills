---
title: Admin & Grants Management
section: admin
---

## Admin & Grants Management

### Grant Management

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants` | GET | List all grants |
| `/v3/grants/{id}` | GET, PATCH, DELETE | Manage a grant |
| `/v3/grants/me` | GET | Get grant by access token |
| `/v3/connect/custom` | POST | Create grant via BYO auth |

Reference: https://developer.nylas.com/docs/dev-guide/best-practices/manage-grants/

### Connectors & Credentials

| Endpoint | Purpose |
|----------|---------|
| `/v3/connectors` | CRUD connectors (Google, Microsoft, etc.) |
| `/v3/connectors/{provider}/creds` | CRUD connector credentials |
| `/v3/providers/detect` | Detect provider by email address |

### API Keys

| Endpoint | Purpose |
|----------|---------|
| `/v3/admin/applications/{application_id}/api-keys` | List/create/delete API keys (Beta; Nylas Service Account auth) |

### Domains

| Endpoint | Purpose |
|----------|---------|
| `/v3/admin/domains` | List/create/delete/verify sending domains (Beta; Nylas Service Account auth) |

### Workspaces

| Endpoint | Purpose |
|----------|---------|
| `/v3/workspaces` | CRUD workspaces for grant organization |

### Applications

| Endpoint | Purpose |
|----------|---------|
| `/v3/applications` | Get/update application settings |
| `/v3/applications/redirect-uris` | Manage callback URIs |

Reference: [Admin API](https://developer.nylas.com/docs/api/v3/admin/)
