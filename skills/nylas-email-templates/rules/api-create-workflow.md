---
title: Create and Test a Workflow
section: api
---

## Create and Test a Workflow

There's no endpoint that fires a workflow on demand, and webhook test notifications don't run workflows. To test with a real trigger without emailing every user, start narrow:

1. **Create a grant-level workflow on a test grant** you control, enabled. It fires only for that grant.
2. **Trigger the event for real:** make a booking, create an event, or revoke access at the provider to fire `grant.expired`, which arrives within minutes.
3. **Check the result:** that the email arrived from the expected sender, looked right, and reached the expected people. Then delete the test workflow.
4. **Create the application-level workflow** with `is_enabled: false` (the API defaults to `true`), and enable it when you're ready.

```bash
curl -s -X POST "$NYLAS_API_URI/v3/workflows" \
  -H "Authorization: Bearer $NYLAS_API_KEY" -H "Content-Type: application/json" \
  -d '{
    "name": "Booking confirmed",
    "trigger_event": "booking.created",
    "template_id": "<TEMPLATE_ID>",
    "delay": 0,
    "is_enabled": false,
    "from": { "email": "bookings@yourdomain.com", "name": "Your Company" }
  }' | jq -r '.data.id'
```

- **Required fields:** `name`, `trigger_event`, and `template_id`.
- **`delay`:** in minutes, where `0` sends immediately.
- **Without `from`:** the workflow sends from the triggering grant.
- **Enabling it:** `PUT /v3/workflows/{workflow_id}` with `{ "is_enabled": true }`.
- **Grant-level workflows:** they can use an application-level or a grant-level template, but a workflow with `from` must use an application-level one.

**Setup some triggers need:**
- **Scheduler `booking.*`:**
  - Set `event_booking.disable_emails: true` on the configuration, or guests also get Scheduler's own email.
  - `notify_participants: true` adds the provider's calendar invitation. Microsoft always sends it regardless.
  - `PUT` replaces `scheduler.additional_fields` as a whole, so include the existing fields when you add `notify_individually`.
- **`booking.reminder`:** only fires if the configuration has `event_booking.reminders: [{ "type": "webhook", "minutes_before_event": 30 }]`. Group configurations put it in `group_booking`.
- **`booking.pending`:** needs `booking_type: "organizer-confirmation"`, which also requires `scheduler.organizer_confirmation_url`.
- **Group bookings:** each new attendee who joins sends the confirmation again to every existing attendee. Reminders fire once per session.
- **`grant.expired` and `grant.deleted`:** need `from`. `grant.expired` fires once, when a grant goes from valid to invalid. Grants that were already invalid don't fire.

Reference: https://developer.nylas.com/docs/reference/api/application-level-workflows/create-workflow/
