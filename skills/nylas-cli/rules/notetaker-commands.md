---
title: Notetaker Commands
section: notetaker
---

## Notetaker (AI Meeting Bot)

```bash
nylas notetaker list                         # List notetakers
nylas notetaker list --state scheduled       # Filter by state
nylas notetaker list --limit 10              # Limit results
nylas notetaker create --meeting-link URL    # Create a notetaker
nylas notetaker create --meeting-link URL --join-time "tomorrow 2pm"
nylas notetaker create --meeting-link URL --bot-name "Meeting Recorder"
nylas notetaker show <id>                    # Show notetaker details
nylas notetaker media <id>                   # Show recording and transcript links
nylas notetaker delete <id>                  # Cancel a notetaker
nylas notetaker delete <id> --force          # Skip confirmation
nylas nt list                                # Alias for list
nylas bot create --meeting-link URL          # Alias for create
```

Use this section for Nylas Notetaker bots that join meetings to record and transcribe. The CLI supports Zoom, Google Meet, and Microsoft Teams, and `nylas notetaker list --state` currently accepts `scheduled`, `connecting`, `attending`, `complete`, `cancelled`, and `failed`. Route `nylas notetaker`, `nylas nt`, and `nylas bot` questions here.
