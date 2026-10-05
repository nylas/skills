---
title: Strict Mode and Guards
section: template
---

## Strict Mode and Guards

The renderer runs in **strict mode**. Any variable the payload doesn't have throws, the render returns `400`, and no email is sent, while the booking or event that caused the trigger still succeeds.

- **Guard everything that can be missing,** and give every guard an `{{else}}` fallback.
- **Guard both levels of a nested path.** `{{#if parent.leaf}}` throws when `parent` is missing:
  ```handlebars
  {{#if recipient}}{{#if recipient.first_name}}Hi {{recipient.first_name}},{{else}}Hi,{{/if}}{{else}}Hi,{{/if}}
  ```
- **Empty is not missing.** Empty strings render without error, so `Hi {{recipient.first_name}},` can come out as "Hi ,". A `lookup` with no matching key renders blank too. `{{#if}}` treats `""` as false. `guest_timezone` and `location` are often `""` on Scheduler bookings.
- **The helpers are** `if`, `unless`, `each`, `with`, `lookup`, `log`, and Nylas' `eq`, `ne`, and `formatDate`.
  - There's no `or`, `and`, `gt`, or `lt`, and there are no string helpers. Write one branch per value, and compute anything else in your own code.
  - `{{else if (eq ...)}}` chains work. `eq` on a missing top-level variable is false, but `(eq parent.leaf "x")` throws when `parent` is missing.
- **Flags from your own code:** pass them as the strings `"true"` or `""`.
- **Engine:** always set `engine: "handlebars"`. The API default is `mustache`, which has no helpers.

Reference: https://developer.nylas.com/docs/v3/email/templates-workflows/#which-helper-functions-can-i-use
