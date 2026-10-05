---
title: Custom Values from Metadata
section: template
---

## Custom Values from Metadata

- **Scheduler bookings:** they carry the configuration's hidden `metadata` fields in `booking_info.additional_fields`, for example a `logo_url`.
  - The page sends whatever the guest's browser submits, so never use these values for routing, pricing, or secrets.
  - API bookings carry only what the request passed.
  - Group-event reminders carry `additional_fields: null`.
- **Events:** they carry the event's `metadata` object, written by your code through the Events API. Don't overwrite keys Scheduler sets on its own events.
- **Guards:** guard each value at both levels and give it a default.
- **Images:** host them anywhere you like. Only the URL goes in the field.

Reference: https://developer.nylas.com/docs/cookbook/workflows/metadata-in-workflows/
