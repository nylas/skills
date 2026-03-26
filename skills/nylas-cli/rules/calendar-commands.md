---
title: Calendar Commands
section: calendar
---

## Calendar Commands

```bash
nylas calendar list                           # List calendars
nylas calendar events list [--days N]         # Upcoming events
nylas calendar events show <id>               # Event details
nylas calendar events create --title T --start S --end E
nylas calendar events update <id>             # Update event
nylas calendar events delete <id>             # Delete event
nylas calendar events rsvp <id> --status yes  # RSVP
nylas calendar availability check             # Check availability
nylas calendar find-time --participants P --duration D
```

### AI Scheduling

```bash
nylas calendar schedule ai "meeting with John next Tuesday afternoon"
nylas calendar analyze                        # AI calendar analytics
nylas calendar ai conflicts --days N          # Detect conflicts
nylas calendar ai reschedule <id>             # AI rescheduling
```
