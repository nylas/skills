---
title: Calendar Commands
section: calendar
---

## Calendar Commands

```bash
nylas calendar list                           # List calendars
nylas calendar show|create|update|delete <id> # Calendar (resource) CRUD
nylas calendar resources                      # List bookable room/equipment resources
nylas calendar events list [--days N]         # Upcoming events
nylas calendar events show <id>               # Event details
nylas calendar events create --title T --start S --end E
nylas calendar events update <id>             # Update event
nylas calendar events delete <id>             # Delete event
nylas calendar events import <calendar-id>    # Bulk-export events (migration/backup)
nylas calendar events rsvp <id> --status yes  # RSVP
nylas calendar recurring list|update|delete   # Recurring-event series
nylas calendar virtual list|show|create|delete  # Virtual calendars
nylas calendar availability check             # Check availability
nylas calendar find-time --participants P --duration D
nylas timezone list|convert|dst|find-meeting|info  # Timezone and DST helpers
```

### AI Scheduling

```bash
nylas calendar schedule ai "meeting with John next Tuesday afternoon"
nylas calendar ai analyze                     # AI calendar analytics
nylas calendar ai analyze-thread              # Suggest meeting times from an email thread
nylas calendar ai conflicts check --title T --start RFC3339 --duration 30
nylas calendar ai reschedule ai <event-id>    # AI rescheduling
nylas calendar ai adapt                       # Adapt schedule to changes
nylas calendar ai focus-time                  # Find/block focus time
```

Current calendar workflows use `find-time` for availability scoring with working-hours inputs, but break protection, DST override handling, and timezone locking belong to event create/update flows plus the dedicated `nylas timezone` commands. When a question crosses into timezone handling, point to the timezone tools directly instead of treating it as part of `find-time`.
