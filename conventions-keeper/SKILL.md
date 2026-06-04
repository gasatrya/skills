---
name: conventions-keeper
description: Create and maintain a project's AGENTS.md — the plain-Markdown "README for agents" at the repo root that records build/test commands, conventions, architecture, and gotchas so coding agents follow them consistently. Use when setting up agent guidance for a repo, when the user says agents keep forgetting or violating project conventions, after conventions or tooling change, or when onboarding an unfamiliar codebase. Pairs with the planning, implementation, and review skills, which all defer to AGENTS.md as the source of truth.
---

# Conventions Keeper

Create and maintain the project's `AGENTS.md` — a plain-Markdown file at the repo root that gives coding agents the build commands, conventions, and tribal knowledge a senior teammate would. It's the source of truth the planning, implementation, and review skills defer to, so its quality sets a ceiling on theirs.

## The one principle that matters

High signal, or nothing. Auto-generated, padded context files have been shown to *lower* agent success and raise cost — only content a developer would actually write earns its place. So AGENTS.md must contain only what is **true, non-obvious, and not already expressed elsewhere**. If a linter, `tsconfig`, ESLint rule, or the README already enforces or states something, leave it out — duplicating it is worse than omitting it.

Keep: exact commands, real conventions the code already follows, architecture orientation, security gotchas, and decisions an agent can't infer from the repo. Cut: vague advice ("write clean code"), style rules a formatter enforces, library bans a config enforces, and codebase summaries the agent can read for itself.

## Creating an AGENTS.md

1. **Derive, don't invent.** Read the codebase first and record what's actually true — the real test command, the real folder convention, the pattern the code already follows. Don't prescribe conventions the project doesn't use.
2. **Draft from the section menu**, including only sections with real content. There's no required heading set or order — use what fits the project.
3. **Verify with the user.** Developer-confirmed beats agent-generated. Show the draft and confirm each claim is accurate before writing the file.

### Section menu (pick what applies)
- **Setup & commands** — install, dev server, build, test, lint, typecheck. Exact and copy-pasteable.
- **Code style & conventions** — only the non-obvious, project-specific rules (naming, file organization, state patterns) a formatter doesn't already enforce.
- **Architecture overview** — a short map of major modules and how they relate. Orientation, not documentation.
- **Testing** — how and what to test, where tests live, how to run a single test.
- **Security & secrets** — what must never be committed, protected paths, where env vars live.
- **Git & PR conventions** — branch naming, commit format, PR title/description expectations.
- **Gotchas** — surprising behavior, sharp edges, things that have bitten people before.

Be concrete: "keep functions to one responsibility; see `src/services/` for the pattern" beats "write modular code." A short code example helps where a rule is easier shown than told.

## Monorepos and multi-stack repos

AGENTS.md nests. Put a root file with shared defaults and a more specific one inside each package or stack — for example, a web app and a WordPress plugin living in the same repo. Agents read the nearest file walking up from whatever they're editing, and the closest one wins on conflicts, so the root holds what's universal and each package overrides only what differs.

## Maintaining it

Conventions drift, and tooling absorbs rules over time. Prune periodically: if a rule has since moved into a linter, formatter, or `tsconfig`, delete it here — its job now belongs to the toolchain. When a real convention changes, update AGENTS.md in the same change so it never lies. A stale file is worse than none, because every skill that trusts it inherits the error.
