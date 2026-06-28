---
title: Scheduler API
section: scheduler
---

## Scheduler API

**Use the Scheduler API over custom availability logic.**

### Endpoints

| Endpoint | Purpose |
|----------|---------|
| `/v3/scheduling/configurations` | CRUD scheduling configurations |
| `/v3/scheduling/sessions` | Create booking sessions |
| `/v3/scheduling/availability` | Check scheduling availability |
| `/v3/scheduling/bookings` | Create/manage bookings |

### Features

| Feature | Doc Link |
|---------|----------|
| Hosted scheduling pages | https://developer.nylas.com/docs/v3/scheduler/hosted-scheduling-pages/ |
| Custom booking flows | https://developer.nylas.com/docs/v3/scheduler/customize-booking-flows/ |
| Meeting types (1:1, group, round-robin) | https://developer.nylas.com/docs/v3/scheduler/meeting-types/ |
| Managing availability | https://developer.nylas.com/docs/v3/scheduler/managing-availability/ |
| Add conferencing | https://developer.nylas.com/docs/v3/scheduler/add-conferencing/ |
| Localization | https://developer.nylas.com/docs/v3/scheduler/localization/ |
| Notetaker integration | https://developer.nylas.com/docs/v3/scheduler/scheduler-notetaker-integration/ |
| Customize appearance | https://developer.nylas.com/docs/v3/scheduler/customize-scheduler/ |

### Timezone & Read-Only Fields

- **Availability timezone precedence** (highest → lowest): participant `open_hours[].timezone` → participant `timezone` → `event_booking.timezone` → `availability_rules.default_open_hours[].timezone`.
- **Hosted pages:** set the guest's initial timezone with the `timezone` URL param (IANA name, e.g. `?timezone=America/New_York`); the guest can still change it.
- **Self-hosted component:** pre-fill and lock guest fields via `bookingInfo` — `primaryParticipant.nameReadOnly`, `primaryParticipant.emailReadOnly`, and `additionalFields[].readOnly`.

### UI Components

70+ embeddable web components for scheduling:

| Component | Doc Link |
|-----------|----------|
| Scheduling component | https://developer.nylas.com/docs/v3/scheduler/using-scheduling-component/ |
| Scheduler editor | https://developer.nylas.com/docs/v3/scheduler/using-scheduler-editor-component/ |
| All UI components reference | https://developer.nylas.com/docs/reference/ui/ |

Reference: [Scheduler docs](https://developer.nylas.com/docs/v3/scheduler/)
