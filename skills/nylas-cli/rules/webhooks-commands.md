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
nylas webhook rotate-secret <id>              # Rotate the signing secret
nylas webhook verify                          # Verify a webhook signature locally
nylas webhook test send|payload <url>         # Send a test event / inspect payload
nylas webhook pubsub list|show|create|update|delete   # Pub/Sub notification channels
nylas webhook server [--port 8080 --tunnel cloudflared]  # Local server
```
