---
title: OTP Codes
section: otp
---

## OTP Codes

Retrieve and watch one-time-password (2FA) codes that arrive by email in connected accounts. Useful for automating logins from the terminal.

```bash
nylas otp get                                 # Get the latest OTP code (copies to clipboard)
nylas otp get --raw                           # Output only the code (no clipboard, script-friendly)
nylas otp get --no-copy                       # Don't copy to clipboard
nylas otp watch                               # Watch for new OTP codes as they arrive
nylas otp watch --interval 5                  # Poll every 5s (-i; default 10)
nylas otp watch --no-copy
nylas otp list                                # List configured accounts
nylas otp messages [--limit 10]              # Show recent messages (debug; -l)
```

Route `nylas otp` questions here. Codes are read from the active grant's mailbox; pair with `nylas auth switch` to target a specific account.
