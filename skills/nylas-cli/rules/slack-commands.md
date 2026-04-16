---
title: Slack Integration Commands
section: slack
---

## Slack Integration

```bash
nylas slack auth set --token xoxp-...        # Store a Slack user token
nylas slack auth status                      # Check Slack auth status
nylas slack auth remove                      # Remove stored Slack token
nylas slack channels list                    # List channels you can access
nylas slack channels list --all-workspace    # List all workspace channels
nylas slack channels info C01234567890       # Show channel details
nylas slack messages list --channel general  # Read messages from a channel
nylas slack messages list --channel general --thread 1234567890.123456
nylas slack send --channel general --text "Hello team!"   # Send a message
nylas slack reply --channel general --thread 1234567890.123456 --text "Reply"
nylas slack users list                       # List Slack users
nylas slack search --query "project update"  # Search messages
```

Use this section for Slack workspace auth, channel discovery, message reads, sends, thread replies, user lookup, and search. The upstream CLI docs place Slack under its own top-level integration section, so route `nylas slack` questions here rather than through generic email or dashboard commands.
