---
title: Multilingual Templates
section: template
---

## Multilingual Templates

Scheduler passes the guest's language in `booking_info.guest_language`, and the host's in `host_language`.

- **Text:** branch every user-visible string on it, **including the subject**.
- **Dates:** pass it as the `formatDate` locale, so dates follow the language too.
- **Fallback:** the `{{else}}` branch is the default language, and any language you don't handle falls through to it.
- **Editing:** when you change a multilingual template, keep every language it already supports.

```handlebars
{{#if (eq booking_info.guest_language "es")}}Reunión confirmada{{else if (eq booking_info.guest_language "fr")}}Rendez-vous confirmé{{else}}Your meeting is confirmed{{/if}}
```
