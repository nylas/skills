---
title: Authentication Commands
section: auth
---

## Authentication Commands

```bash
nylas auth login                              # Authenticate (Google default)
nylas auth login --provider microsoft         # Microsoft/Outlook
nylas auth config                             # Configure API credentials
nylas auth list                               # List connected accounts
nylas auth show [grant-id]                    # Show account details
nylas auth status                             # Check auth status
nylas auth whoami                             # Show current identity
nylas auth switch <email-or-grant-id>         # Switch the active/default account
nylas auth logout                             # Logout
nylas auth add <grant-id>                     # Re-add an existing grant locally
nylas auth remove <grant-id>                  # Remove grant from local config only
nylas auth revoke <grant-id>                  # Permanently revoke grant on server
nylas auth token                              # Display API token
nylas auth scopes [grant-id]                  # Show OAuth scopes
nylas auth providers                          # List providers
nylas auth detect <email>                     # Detect provider from email address
nylas auth migrate                            # Migrate credentials to system keyring
```

### Active account with multiple grants

This applies to **every** account type (OAuth Google/Microsoft, IMAP, and `provider=nylas` agent accounts), not just newly created ones. When more than one grant is connected, all commands (`nylas email`, `nylas calendar`, `nylas contacts`, `nylas otp`, …) run against the single **active/default** grant:

- `nylas auth list` — shows every grant; the `DEFAULT` column marks the active one with `✓`.
- `nylas auth whoami` — prints the active account (email + grant ID).
- `nylas auth switch <email-or-grant-id>` — change which grant is active.
- `NYLAS_GRANT_ID=<id> nylas email list` — target a different grant for a single command without switching the default.

Adding or creating an account does not auto-switch — check `nylas auth list` to confirm which one is default before running commands.

**Free-tier limit:** up to **5 grants/accounts total**, across any mix of providers (OAuth Google/Microsoft, IMAP, and `provider=nylas` agent accounts all count toward the same cap); paid plans add more.
