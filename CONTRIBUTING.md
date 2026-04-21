# Contributing to Nylas Skills

## Adding a New Rule

1. Pick the skill (`skills/nylas-api/` or `skills/nylas-cli/`)
2. Copy `rules/_template.md` to `rules/<section>-<description>.md`
3. Choose the section prefix from `rules/_sections.md`
4. Fill in the frontmatter (`title`, `section`) and content
5. Update `SKILL.md` rules section to include the new rule
6. Update `AGENTS.md` with the full content
7. Link to the official doc page using `https://developer.nylas.com/docs/...` URLs

## Rule File Guidelines

- One topic per file
- Use the section prefix consistently (e.g., `auth-`, `email-`, `calendar-`)
- Include endpoint tables for API rules
- Include curl examples and SDK examples (Node.js + Python) where applicable
- Include command examples with inline comments for CLI rules
- Link to official doc URLs as reference material, but keep the checked-in rules and compiled docs as the working source for agent behavior
- Keep each rule focused and self-contained

## Adding a New Skill

1. Create `skills/<skill-name>/` directory
2. Add required files:
   - `SKILL.md` — Frontmatter + concise rules index with doc links
   - `AGENTS.md` — Full compiled reference
   - `CLAUDE.md` — Claude Code auto-loaded context (lean)
   - `README.md` — Contributor guide
   - `LICENSE.txt` — MIT license
   - `rules/_sections.md` — Section definitions
   - `rules/_template.md` — Rule template
3. Update `.claude-plugin/marketplace.json` to include the new skill path
4. Update `.cursor-plugin/marketplace.json` to include the new skill path
5. Update root `README.md` and `AGENTS.md`

## Skill Naming

- **Skill directory**: `kebab-case`, prefixed with `nylas-` (e.g., `nylas-api`, `nylas-cli`)
- **Rule files**: `<section-prefix>-<description>.md` (e.g., `auth-oauth-flow.md`)
- **SKILL.md**: Always uppercase, always this exact filename

## Context Efficiency

- Keep `SKILL.md` under 100 lines — it's the index, not the reference
- `AGENTS.md` has the full compiled reference
- `CLAUDE.md` is auto-loaded — keep it under 30 lines
- Individual `rules/` files are read on demand — don't duplicate across files
- Keep external docs links as reference URLs only; do not instruct agents to fetch remote markdown into the active prompt at runtime
- All doc URLs must use the `/docs/` prefix (e.g., `developer.nylas.com/docs/v3/email/`)
