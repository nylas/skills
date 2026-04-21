---
title: Authentication Flows
section: auth
---

## Authentication Flows

Nylas uses OAuth to connect user accounts. A **grant** represents an authenticated user account.

### Hosted OAuth with API Key (recommended for server-side apps)

1. Create an application in the Nylas Dashboard
2. Set up a connector (Google, Microsoft, etc.) with OAuth credentials
3. Redirect users to Nylas hosted auth URL
4. Nylas creates an unverified grant record after the provider auth succeeds
5. Nylas redirects back to your callback URI with a one-time OAuth `code`
6. Exchange the `code` with `POST /v3/connect/token`
7. After the token exchange succeeds, Nylas marks the grant record as verified and returns a usable `grant_id`

```
GET https://api.us.nylas.com/v3/connect/auth?
  client_id=<NYLAS_CLIENT_ID>
  &redirect_uri=<YOUR_CALLBACK>
  &response_type=code
  &provider=google
  &scope=https://www.googleapis.com/auth/gmail.modify
```

**Important:** Hosted OAuth does not return a usable grant ID directly in the browser redirect. Your backend must exchange the returned `code` at `POST /v3/connect/token`; the token-exchange response includes the usable `grant_id` for subsequent grant-scoped API calls.

### Hosted OAuth with Access Token + PKCE (for SPAs & mobile)

Same redirect flow, but uses PKCE challenge for token exchange. Developer manages token refresh.

### API Authentication (all requests)

```bash
curl -X GET "https://api.us.nylas.com/v3/grants/<GRANT_ID>/messages" \
  -H "Authorization: Bearer <NYLAS_API_KEY>" \
  -H "Content-Type: application/json"
```

### All Auth Methods

| Method | Use Case | Doc Link |
|--------|----------|----------|
| Hosted OAuth (API key) | Server-side web apps | https://developer.nylas.com/docs/v3/auth/hosted-oauth-apikey/ |
| Hosted OAuth (access token + PKCE) | SPAs and mobile apps | https://developer.nylas.com/docs/v3/auth/hosted-oauth-accesstoken/ |
| Bring Your Own Auth (BYO) | Already have OAuth tokens | https://developer.nylas.com/docs/v3/auth/bring-your-own-authentication/ |
| IMAP Auth | IMAP providers without OAuth | https://developer.nylas.com/docs/v3/auth/imap/ |
| Service Accounts | Google Workspace admin access | https://developer.nylas.com/docs/provider-guides/google/google-workspace-service-accounts/ |
| Nylas Connect | Embeddable auth button (React) | https://developer.nylas.com/docs/v3/auth/nylas-connect/ |
| Bulk Auth | Migrate many grants at once | https://developer.nylas.com/docs/v3/auth/bulk-auth-grants/ |
| Multiple Providers | One app, multiple connectors | https://developer.nylas.com/docs/v3/auth/using-multiple-provider-applications/ |

### Grant Lifecycle

- Grants can expire when provider tokens become invalid
- Monitor `grant.expired` webhooks to trigger re-authentication
- Re-authenticating preserves the grant ID and sync state

**For detailed auth flows, use WebFetch on the doc links above.**

Reference: [Auth overview](https://developer.nylas.com/docs/v3/auth/) | [Troubleshooting](https://developer.nylas.com/docs/v3/auth/troubleshooting/)
