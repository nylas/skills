---
title: Email Commands
section: email
---

## Email Commands

```bash
nylas email list [grant-id]                   # Recent emails
nylas email read <id>                         # Read a message
nylas email send --to EMAIL --subject S --body B [--sign] [--encrypt]
nylas email search "invoice"                  # Search
nylas email delete <id>                       # Delete
nylas email mark read|starred <id>            # Mark message
nylas email smart-compose --prompt "..."      # AI email generation
nylas email ai analyze [--unread]             # AI inbox summary
nylas email metadata show <id>                # Show message metadata
nylas email attachments list <id>             # List attachments
nylas email folders list                      # List folders
nylas email threads list                      # List threads
nylas email drafts list                       # List drafts
nylas email templates list                    # List local templates
nylas email templates create --name NAME --subject SUBJECT --body BODY
nylas email templates show <template-id>      # Show local template details
nylas email templates update <template-id>    # Update a local template
nylas email templates delete <template-id>    # Delete a local template
nylas email templates use <template-id> --to EMAIL
nylas template list                           # List hosted templates
nylas template create --name NAME --subject SUBJECT --body BODY
nylas template show <template-id>             # Show hosted template details
nylas template update <template-id>           # Update a hosted template
nylas template delete <template-id> --yes     # Delete a hosted template
nylas template render <template-id> --data '{}'
nylas template render-html --body "<p>{{x}}</p>" --engine mustache --data '{}'
nylas email scheduled list                    # List scheduled sends
```

**Filters:** `--unread`, `--starred`, `--from`, `--to`, `--subject`, `--has-attachment`

Managed transactional send uses the grant's sender automatically for `inbox` and `nylas` providers, and it does not support GPG signing/encryption or `--signature-id`. Keep that distinction in mind when explaining send workflows.
