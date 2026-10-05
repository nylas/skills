# nylas-hol-guard

Use HOL Guard as an optional local pre-execution safety boundary before a supported AI coding-agent harness performs state-changing Nylas work.

## What this skill covers

- installs and initializes the published `hol-guard` package with user approval;
- verifies the supported local harness and current Guard status;
- launches the coding agent through HOL Guard before Nylas mutations;
- applies to email, calendar, contact, webhook, Agent Account, and administrative changes;
- preserves Nylas authentication, grant scopes, policies, confirmations, API validation, and audit logging as authoritative controls.

## Structure

```
SKILL.md
CLAUDE.md
AGENTS.md
metadata.json
rules/
  _sections.md
  _template.md
  setup-hol-guard.md
  safety-mutations.md
```

## References

- Nylas API: https://developer.nylas.com/docs/api/v3/
- Nylas Agent Accounts: https://developer.nylas.com/docs/v3/agent-accounts/
- HOL Guard setup: https://github.com/hashgraph-online/hol-guard/blob/main/docs/guard/get-started.md

## Contributing

See [CONTRIBUTING.md](../../CONTRIBUTING.md) for repository contribution rules.
