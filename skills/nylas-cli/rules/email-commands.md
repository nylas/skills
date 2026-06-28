---
title: Email Commands
section: email
---

## Email Commands

```bash
nylas email list [grant-id]                   # Recent emails
nylas email read <id>                         # Read a message
nylas email send --to EMAIL --subject S --body B [--sign] [--encrypt]
nylas email reply <id> --body B               # Reply to a message
nylas email search "invoice"                  # Search
nylas email move <id> --folder F              # Move to a folder (or archive)
nylas email clean <id>                        # Strip quoted replies/signatures from a message
nylas email delete <id>                       # Delete
nylas email mark read|unread|starred|unstarred <id>   # Mark message
nylas email tracking-info <id>                # Open/click/reply tracking for a message
nylas email smart-compose --prompt "..."      # AI email generation
nylas email ai analyze [--unread]             # AI inbox summary
nylas email metadata show|info <id>           # Show message metadata (info = field reference)
nylas email attachments list|show|download <id>       # Attachments
nylas email folders list|create|show|rename|delete    # Folders
nylas email signatures list|create|show|update|delete # Stored signatures
nylas email threads list|show|search|mark|delete      # Threads
nylas email drafts list|create|show|send|delete       # Drafts
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
nylas email scheduled list|show|cancel        # Scheduled sends
```

**Filters:** `--unread`, `--starred`, `--from`, `--to`, `--subject`, `--has-attachment`

Managed transactional send uses the grant's sender automatically for `inbox` and `nylas` providers, and it does not support GPG signing/encryption or `--signature-id`. Keep that distinction in mind when explaining send workflows.
