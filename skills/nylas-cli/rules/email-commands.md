---
title: Email Commands
section: email
---

## Email Commands

```bash
nylas email list [grant-id]                   # Recent emails
nylas email read <id>                         # Read a message
nylas email send --to EMAIL --subject S --body B [--sign] [--encrypt]
nylas email search --query "invoice"          # Search
nylas email delete <id>                       # Delete
nylas email mark read|starred <id>            # Mark message
nylas email smart-compose --prompt "..."      # AI email generation
nylas email ai analyze [--unread]             # AI inbox summary
nylas email metadata show <id>                # Show message metadata
nylas email attachments list <id>             # List attachments
nylas email folders list                      # List folders
nylas email threads list                      # List threads
nylas email drafts list                       # List drafts
nylas email templates list                    # List templates
nylas email scheduled list                    # List scheduled sends
```

**Filters:** `--unread`, `--starred`, `--from`, `--to`, `--subject`, `--has-attachment`
