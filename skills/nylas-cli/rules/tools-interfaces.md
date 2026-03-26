---
title: Tools & Interfaces
section: tools
---

## Interfaces

| Command | Description |
|---------|-------------|
| `nylas tui` | Interactive terminal UI with vim keys |
| `nylas ui` | Alternate UI launcher |
| `nylas air` | Web client at localhost:7365 |
| `nylas demo <resource>` | Try without an account |

## Timezone Utilities (Offline)

```bash
nylas timezone list [--filter America]        # List timezones
nylas timezone convert --from PST --to EST    # Convert time
nylas timezone dst --zone America/New_York    # DST info
nylas timezone find-meeting --zones "NYC,London,Tokyo"  # Find meeting times
nylas timezone info <zone>                    # Timezone details
```
