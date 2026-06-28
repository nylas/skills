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

### Domains (inbox / agent-account domains)

Manage `*.nylas.email` and custom inbox domains used by agent accounts (see [`agent-commands.md`](agent-commands.md)).

```bash
nylas dashboard domains list                  # List inbox domains
nylas dashboard domains check <subdomain>     # Check subdomain availability
nylas dashboard domains create <domain> --region us|eu   # Register a domain
nylas dashboard domains show <domain-id>      # Domain details
nylas dashboard domains dns <domain-id>       # Show DNS records required for verification
nylas dashboard domains verify <domain-id>    # Verify domain DNS
nylas dashboard domains update <domain-id>    # Update a domain
nylas dashboard domains delete <domain-id> --yes
```

### Organizations

```bash
nylas dashboard orgs list                     # List organizations
nylas dashboard orgs switch                   # Switch organization
```
