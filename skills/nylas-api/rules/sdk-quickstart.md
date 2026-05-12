---
title: SDK Quick Start
section: sdk
---

## SDK Quick Start

### Node.js (`npm install nylas`)

```typescript
import Nylas from "nylas";
const nylas = new Nylas({
  apiKey: "NYLAS_API_KEY",
  apiUri: "https://api.us.nylas.com",
});

// Send email from explicit application input.
await nylas.messages.send({
  identifier: "GRANT_ID",
  requestBody: {
    subject: "Hello",
    body: "Message body",
    to: [{ email: "recipient@example.com" }],
  },
});
```

### Python (`pip install nylas`)

```python
from nylas import Client
nylas = Client("NYLAS_API_KEY", "https://api.us.nylas.com")

# Send email from explicit application input.
nylas.messages.send(
    "GRANT_ID",
    request_body={
        "subject": "Hello",
        "body": "Message body",
        "to": [{"email": "recipient@example.com"}],
    },
)
```

### Ruby (`gem install nylas`)

```ruby
require "nylas"
nylas = Nylas::Client.new(api_key: "NYLAS_API_KEY")
```

### All SDKs

| SDK | Install | Doc Link |
|-----|---------|----------|
| Node.js | `npm install nylas` | https://developer.nylas.com/docs/v3/sdks/ |
| Python | `pip install nylas` | https://developer.nylas.com/docs/v3/sdks/ |
| Ruby | `gem install nylas` | https://developer.nylas.com/docs/v3/sdks/ |
| Kotlin/Java | Maven/Gradle | https://developer.nylas.com/docs/v3/sdks/ |

Reference: [SDK docs](https://developer.nylas.com/docs/v3/sdks/)
