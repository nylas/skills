---
title: Escaping and Links
section: template
---

## Escaping and Links

- **Escaping:** `{{ }}` HTML-escapes values, including inside an `href`. `&` becomes `&amp;`, which mail clients decode. `{{{ }}}` renders raw HTML.
- **Use triple braces only** for fields documented as HTML, or for Send API values you sanitized yourself.
- **`booking_info.event_description` is HTML,** and it already includes Scheduler's own reschedule and cancel links. Don't show it alongside your own buttons for the same actions.
- **Links from metadata are escaped but not validated.** Only put an `https://` URL your app wrote into an `href`, and never a value a guest typed.
