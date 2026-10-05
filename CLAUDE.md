# Nylas Skills

Skills for building with the Nylas platform. v3 only — v2 is deprecated.

## Skills

| Skill | Trigger | Use when |
|-------|---------|----------|
| `nylas-api` | `nylas`, `@nylas/nylas`, `nylas-python` imports | Building API integrations |
| `nylas-cli` | `nylas init`, `nylas email`, `nylas mcp` mentions | Running CLI commands |
| `nylas-hol-guard` | state-changing Nylas work from a supported local AI harness | Launching the agent through HOL Guard before mutations |

## Structure

Each skill: `SKILL.md` (index) → `rules/` (on demand) → `AGENTS.md` (full reference).

Docs: `https://developer.nylas.com/llms.txt` | Contributing: [CONTRIBUTING.md](CONTRIBUTING.md)
