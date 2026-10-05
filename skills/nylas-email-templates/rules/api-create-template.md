---
title: Create a Template
section: api
---

## Create a Template

The `body` field is a JSON string, so let `jq` escape it. **Set `engine: "handlebars"` explicitly.** The default, `mustache`, fails on `formatDate` and `lookup`, and `nunjucks` and `twig` aren't accepted.

```bash
jq -n --rawfile body template.html \
  '{name: "Booking confirmed", engine: "handlebars", subject: "Confirmed: {{booking_info.title}}", body: $body}' \
| curl -s -X POST "$NYLAS_API_URI/v3/templates" \
    -H "Authorization: Bearer $NYLAS_API_KEY" -H "Content-Type: application/json" -d @- \
| jq -r '.data.id'
```

- **Required fields:** `name`, `subject`, and `body`. The response's `data.id` is the template ID.
- **Grant-level templates:** post to `/v3/grants/{grant_id}/templates` instead.
- **Comments:** Handlebars comments (`{{!-- ... --}}`) are stored with the body and stripped at render time.

Reference: https://developer.nylas.com/docs/reference/api/application-level-templates/create-app-level-template/
