---
title: Render-Test a Template
section: api
---

## Render-Test a Template

`POST /v3/templates/render` renders a template without storing it, using the same strict renderer as workflows. Test against a realistic payload, then with optional fields removed or `""`, and with every custom metadata key present.

```bash
# Body
jq -n --rawfile body template.html --slurpfile vars payload.json \
  '{engine: "handlebars", strict: true, body: $body, variables: $vars[0]}' \
| curl -s -X POST "$NYLAS_API_URI/v3/templates/render" \
    -H "Authorization: Bearer $NYLAS_API_KEY" -H "Content-Type: application/json" -d @-

# Subject
jq -n --arg subject 'Confirmed: {{booking_info.title}}' --slurpfile vars payload.json \
  '{engine: "handlebars", strict: true, body: $subject, variables: $vars[0]}' \
| curl -s -X POST "$NYLAS_API_URI/v3/templates/render" \
    -H "Authorization: Bearer $NYLAS_API_KEY" -H "Content-Type: application/json" -d @-
```

- **Output:** the rendered HTML is in the response's `data`.
- **A stored template:** test it with `POST /v3/templates/{template_id}/render`, which takes `{ "strict": true, "variables": {...} }`.
- **Errors:** a `400` names the variable that failed:

  | Message | Template | Cause |
  |---|---|---|
  | `"first_name" not defined in undefined` | `{{recipient.first_name}}` | The parent (`recipient`) is missing |
  | `Cannot read properties of undefined (reading 'first_name')` | `{{#if recipient.first_name}}` | The parent is missing, inside a guard |
  | `"first_name" not defined in [object Object]` | `{{first_name}}` | The top-level variable is missing |

- **The Dashboard's template preview** fills placeholders with text, so it can't check `formatDate` or `{{#if}}` logic. Use the render endpoint instead.

Reference: https://developer.nylas.com/docs/reference/api/application-level-templates/render-template-html/
