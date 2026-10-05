---
title: recipient and notify_individually
section: payload
---

## recipient and notify_individually

`recipient.email`, `recipient.first_name`, and `recipient.last_name` are added only when a message goes to exactly one person. The name is split at the first space.

- **Scheduler bookings:** for one message per participant, set `notify_individually` to exactly the string `"true"` in the booking's `additional_fields`. The boolean `true` and `"True"` are ignored.
  - The configuration must declare it first, as a hidden `metadata` additional field, or the booking returns `400 Additional field 'notify_individually' not found in configuration`.
  - The hosted scheduling page sends the field's `default`. Bookings made through the Bookings API must pass the value themselves.
- **Events:** for one message per participant, set `"notify_individually": "true"` in the event's `metadata`. Without it, `event.created` sends one message to all participants, with no `recipient`.
- **Everywhere else**, including group bookings, treat `recipient` as optional and guard it.

In every copy of a booking email, `booking_info` is identical and only `recipient` changes, and no field marks which participant is the host. For per-recipient values such as timezones, key a dictionary on email address and read it with `{{lookup booking_info.additional_fields recipient.email}}`.

Reference: https://developer.nylas.com/docs/v3/email/templates-workflows/#notify-individual-participants
