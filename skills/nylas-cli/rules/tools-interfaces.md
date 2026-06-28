---
title: Tools & Interfaces
section: tools
---

## Interfaces

| Command | Description |
|---------|-------------|
| `nylas tui` | Interactive terminal UI with vim keys |
| `nylas tui messages\|events\|contacts\|grants\|webhooks` | Launch TUI directly to a specific view |
| `nylas tui theme init\|list\|set-default\|validate` | Manage TUI themes |
| `nylas ui` | Alternate UI launcher |
| `nylas air` | Web client at localhost:7365 |
| `nylas demo <resource>` | Try without an account |

## Command Metadata

```bash
nylas commands                                # Flat list of commands for browsing
nylas commands --json                         # Machine-readable command/flag schema for agents
nylas commands email send --json              # Schema for a specific command path
nylas commands --all --format yaml            # Include hidden commands/flags
```

## Timezone Utilities (Offline)

```bash
nylas timezone list [--filter America]        # List timezones
nylas timezone convert --from PST --to EST    # Convert time
nylas timezone dst --zone America/New_York    # DST info
nylas timezone find-meeting --zones "NYC,London,Tokyo"  # Find meeting times
nylas timezone info <zone>                    # Timezone details
```
