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
nylas auth switch                             # Switch active account
nylas auth logout                             # Logout
nylas auth remove                             # Remove account
nylas auth token                              # Display API token
nylas auth scopes [grant-id]                  # Show OAuth scopes
nylas auth providers                          # List providers
nylas auth migrate                            # Migrate account
```
