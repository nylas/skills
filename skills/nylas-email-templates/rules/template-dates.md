---
title: Dates and Timezones
section: template
---

## Dates and Timezones

`{{formatDate timestamp timezone "DDDD, t ZZZZ" locale}}`. All 4 arguments can be variables.

- **Timestamps are Unix seconds.** A few Notetaker fields, such as `join_time`, are milliseconds.
- **The timezone is an IANA name.**
  - An empty timezone silently renders UTC, and an invalid one fails the whole render.
  - For bookings, fall back from `guest_timezone` to `organizer_timezone`, which is the configuration's timezone.
- **The format uses Luxon tokens:** `DDDD` is the full localized date and `t` is the localized time.
- **Missing arguments:** a missing timestamp or locale fails the render. Pass `null` for an optional argument you skip.
- **Event `when` objects** are `timespan`, `date`, or `datespan`.
  - Only `timespan` has timestamps, and `formatDate` throws on date strings, so branch on `when.object` first.
  - A `datespan`'s `end_date` is exclusive.

Reference: https://developer.nylas.com/docs/v3/email/templates-workflows/#format-dates-and-times-in-templates
