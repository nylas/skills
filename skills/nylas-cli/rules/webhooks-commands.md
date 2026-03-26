---
title: Webhook Commands
section: webhooks
---

## Webhook Commands

```bash
nylas webhook list                            # List webhooks
nylas webhook create --url URL --triggers T   # Create webhook
nylas webhook update <id>                     # Update webhook
nylas webhook delete <id>                     # Delete webhook
nylas webhook triggers                        # List available triggers
nylas webhook test send <url>                 # Send test event
nylas webhook server [--port 8080 --tunnel cloudflared]  # Local server
```
