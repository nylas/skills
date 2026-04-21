---
title: Dashboard Management Commands
section: dashboard
---

## Dashboard Management Commands

### Account

```bash
nylas dashboard register                      # Create account (SSO)
nylas dashboard login                         # Log in
nylas dashboard login --google|--microsoft|--github  # SSO providers
nylas dashboard sso login --provider google   # SSO login
nylas dashboard sso register --provider github # SSO registration
nylas dashboard logout                        # Log out
nylas dashboard status                        # Auth status
nylas dashboard refresh                       # Refresh token
```

### Applications

```bash
nylas dashboard apps list                     # List apps
nylas dashboard apps create --name N --region R
nylas dashboard apps use <app-id>             # Switch active app
nylas dashboard apps apikeys list             # List API keys
nylas dashboard apps apikeys create           # Create API key
```

### Organizations

```bash
nylas dashboard orgs list                     # List organizations
nylas dashboard orgs switch                   # Switch organization
```
