# nylas-email-templates

Write, test, and deploy Nylas email templates and workflows with an API key.

## What this skill covers

- **Choosing the approach:** when to use a workflow and when to use the Send API, plus triggers, scope, sender, and recipients
- **Payload and recipients:** template variables, `recipient`, and `notify_individually`
- **Writing templates:** strict-mode guards, dates and timezones, escaping and links, email-safe HTML, multilingual templates, and custom values from metadata
- **API:** render-testing, creating templates and workflows, testing on a test grant, managing them, and sending stored templates
- **Debugging:** workflow logs, sender and domain errors, and duplicates
- **Examples:** the tested templates in [nylas/workflow-email-templates](https://github.com/nylas/workflow-email-templates)

## Structure

```
SKILL.md          # Concise rules index (loaded on activation)
CLAUDE.md         # Claude Code auto-loaded context
AGENTS.md         # Full compiled reference
metadata.json     # Skill metadata for marketplace
rules/            # Individual rule files (read on demand)
  _sections.md    # Rule ordering and priorities
  _template.md    # Template for new rules
```

## Docs source

- **Templates and workflows:** https://developer.nylas.com/docs/v3/email/templates-workflows/
- **Workflow cookbook:** https://developer.nylas.com/docs/cookbook/workflows/

## Contributing

See [CONTRIBUTING.md](../../CONTRIBUTING.md) for how to add or update rules.
