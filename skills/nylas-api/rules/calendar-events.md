---
title: Calendar Events API
section: calendar
---

## Calendar Events API

| Endpoint | Methods | Purpose |
|----------|---------|---------|
| `/v3/grants/{id}/calendars` | GET, POST, PUT, DELETE | CRUD calendars |
| `/v3/grants/{id}/events` | GET, POST, PUT, DELETE | CRUD events |
| `/v3/calendars/availability` | POST | Check availability |
| `/v3/calendars/free-busy` | POST | Check free/busy |
| `/v3/grants/{id}/events/{id}/send-rsvp` | POST | Send RSVP |
| `/v3/grants/{id}/room-resources` | GET | List room resources |

### Advanced Calendar Features

| Feature | Doc Link |
|---------|----------|
| Recurring events | https://developer.nylas.com/docs/v3/calendar/recurring-events/ |
| Virtual calendars | https://developer.nylas.com/docs/v3/calendar/virtual-calendars/ |
| Add conferencing (Zoom, Teams) | https://developer.nylas.com/docs/v3/calendar/add-conferencing/ |
| Group booking | https://developer.nylas.com/docs/v3/calendar/group-booking/ |
| Calendar availability | https://developer.nylas.com/docs/v3/calendar/calendar-availability/ |
| Free/busy check | https://developer.nylas.com/docs/v3/calendar/check-free-busy/ |

Reference: [Calendar docs](https://developer.nylas.com/docs/v3/calendar/)
