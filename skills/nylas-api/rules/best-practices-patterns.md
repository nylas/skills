---
title: Best Practices & Error Handling
section: best-practices
---

## Best Practices

1. **Rate limits** — Implement exponential backoff on 429 responses. See rate limit table below.
2. **Pagination** — Use `page_token` from response `next_cursor` for paginating large result sets.
3. **Webhooks over polling** — Always prefer webhooks for real-time updates.
4. **Error handling** — Check `error.type` and `error.message` in response body.
5. **Scopes** — Request minimal OAuth scopes needed for your use case.
6. **Grant lifecycle** — Monitor `grant.expired` webhooks and re-authenticate users when needed.
7. **search_query_native** — Use provider-native search for complex queries (Gmail operators, Microsoft KQL).
8. **Field selection** — Use `select` parameter to return only needed fields, reducing payload size.
9. **Metadata** — Store up to 50 key-value pairs on messages, events, and other objects.
10. **Threads endpoint** — Makes many provider calls per request. Always use filters and limits.

### Nylas API Rate Limits

| Endpoint | Limit | Window |
|----------|-------|--------|
| Messages | 200 req/grant | 1 second |
| Send (JSON) | 200 req/grant | 1 second |
| Send (Multipart) | 10 req/grant | 1 second |
| Calendar | 200 req/grant | 1 second |
| Contacts | 200 req/grant | 1 second |
| Applications | 50 req/app | 1 second |
| Authentication | 50 req/app | 1 second |
| Connectors | 50 req/app | 1 second |
| Grants | 50 req/app | 1 second |
| Webhooks | 50 req/app | 1 second |

### Provider Rate Limits

| Provider | Limit | Notes |
|----------|-------|-------|
| Google | 10,000 req/min per app, 600 req/min per user | 2,000 messages/day send limit |
| Microsoft | 10,000 req/10 min, 4 concurrent | 30 messages/min send limit |
| iCloud | 1,000 messages/day | — |

### Rate Limit Headers

- `Nylas-Provider-Request-Count` — Call volume to provider APIs
- `Nylas-Gmail-Quota-Usage` — Gmail quota consumption
- `Retry-After` — Seconds to wait (Microsoft, EWS)

### Error Codes

| Series | Meaning | Doc Link |
|--------|---------|----------|
| 200 | Success responses | https://developer.nylas.com/docs/api/errors/200-response/ |
| 400 | Client errors (bad request, auth, not found) | https://developer.nylas.com/docs/api/errors/400-response/ |
| 500 | Server errors | https://developer.nylas.com/docs/api/errors/500-response/ |
| 700 | Provider-specific errors | https://developer.nylas.com/docs/api/errors/700-response/ |

### Detailed Guides

| Topic | Doc Link |
|-------|----------|
| Rate limits | https://developer.nylas.com/docs/dev-guide/platform/rate-limits/ |
| Grant lifecycle | https://developer.nylas.com/docs/dev-guide/best-practices/grant-lifecycle/ |
| Error handling | https://developer.nylas.com/docs/dev-guide/best-practices/error-handling/ |
| Search | https://developer.nylas.com/docs/dev-guide/best-practices/search/ |
| Webhook best practices | https://developer.nylas.com/docs/dev-guide/best-practices/webhook-best-practices/ |
| Spam management | https://developer.nylas.com/docs/dev-guide/best-practices/dealing-with-spam/ |
| Email delivery | https://developer.nylas.com/docs/dev-guide/best-practices/improving-email-delivery/ |
| Field selection | https://developer.nylas.com/docs/dev-guide/platform/field-selection/ |
| Metadata | https://developer.nylas.com/docs/dev-guide/metadata/ |
| Data residency | https://developer.nylas.com/docs/dev-guide/platform/data-residency/ |
| Privacy mode | https://developer.nylas.com/docs/dev-guide/platform/privacy-mode/ |
| Scopes reference | https://developer.nylas.com/docs/dev-guide/scopes/ |

Reference: [All best practices](https://developer.nylas.com/docs/dev-guide/best-practices/) | [All error codes](https://developer.nylas.com/docs/api/errors/)
