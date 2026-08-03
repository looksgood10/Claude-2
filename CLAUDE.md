# CLAUDE.md

Guidance for Claude Code and any agents working in this repository.

> **Template status:** placeholders are marked `<!-- TODO -->`. Delete any section
> that doesn't apply — an empty or stale section is worse than no section.
> Keep this file short. It is prepended to every agent's context, so every line
> costs tokens on every turn. Aim for under ~200 lines.

---

## Project overview

<!-- TODO: 2–4 sentences. What this project does, who uses it, what problem it solves.
     Enough that an agent with zero prior context knows what it's touching. -->

**Status:** <!-- TODO: prototype / active development / production -->

---

## Commands

The commands an agent needs to verify its own work. Keep this list to what you
actually run — not everything in `package.json`.

```bash
# Install
<!-- TODO -->

# Run locally
<!-- TODO -->

# Test
<!-- TODO -->

# Test a single file (agents need this — full suites are slow)
<!-- TODO -->

# Lint / format
<!-- TODO -->

# Typecheck
<!-- TODO -->

# Build
<!-- TODO -->
```

**Before declaring work complete, run:** <!-- TODO: e.g. `npm run lint && npm test` -->

---

## Architecture

<!-- TODO: The things that are NOT obvious from reading a single file.
     Good entries:
       - How data flows through the system, end to end
       - Module boundaries and what may import what
       - Where the important abstractions live and why
       - Non-obvious coupling between components
     Skip: a directory listing. Agents can run `ls`. -->

### Key directories

| Path | Purpose |
| --- | --- |
| `<!-- TODO -->` | <!-- TODO --> |

---

## Conventions

<!-- TODO: only rules a competent engineer would NOT guess from reading the code.
     Delete the examples below and replace with real ones. -->

- **Naming:** <!-- TODO -->
- **Error handling:** <!-- TODO -->
- **Testing:** <!-- TODO: framework, where tests live, what must be covered -->
- **Imports:** <!-- TODO: e.g. absolute from `src/`, no deep relative paths -->

### Do not

<!-- TODO: hard constraints. These are the highest-value lines in this file —
     they prevent the mistakes that cost you a review cycle. Examples:
       - Do not edit `<generated file>` — regenerate with `<command>`
       - Do not add dependencies without asking
       - Do not commit directly to `main` -->

---

## Git workflow

- **Branch from:** <!-- TODO: e.g. `main` -->
- **Branch naming:** <!-- TODO: e.g. `feat/short-description` -->
- **Commits:** <!-- TODO: e.g. Conventional Commits -->
- Do not commit or push unless asked.

---

## Environment & secrets

- Required environment variables are documented in <!-- TODO: e.g. `.env.example` -->
- Never commit `.env`, credentials, tokens, or keys.
- Never print secret values into logs, commit messages, or PR descriptions.

---

## Agents and skills

Custom agents, skills, and commands for this repo live under `.claude/`:

```
.claude/
├── agents/      # Subagent definitions (one .md per agent, YAML frontmatter)
├── skills/      # Reusable skills (SKILL.md + supporting files)
├── commands/    # Slash commands (one .md per command)
└── settings.json # Shared permissions, hooks, env
```

Notes for building these out:

- A **subagent** gets its own fresh context. Use one when a task is genuinely
  separable and you only need its conclusion — not to parallelize work that
  needs shared context.
- A **skill** is instructions loaded on demand. Its `description` is what
  determines whether it triggers, so write that field for matching, not for prose.
- **Automated behaviors** ("always run X after editing a file") belong in
  `settings.json` hooks, not in this file. Instructions here are advisory;
  hooks are enforced by the harness.
- Put machine-specific or personal settings in `.claude/settings.local.json`
  and gitignore it.

<!-- TODO: list the agents/skills specific to this project once they exist -->

---

## Writing rules for this file

Keep this file working by holding to a few rules:

1. **Be specific and testable.** "Use `Result<T>` for fallible functions" beats
   "handle errors properly."
2. **Document the surprising, not the standard.** If it's true of every project
   in this language, leave it out.
3. **Update it when it goes stale.** A wrong instruction here actively misleads
   every future agent; that's more expensive than a missing one.
4. **Scope narrowly.** Rules for one subtree belong in a nested `CLAUDE.md` in
   that directory, not here.
