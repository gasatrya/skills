---
name: commit-and-pr
description: Write commit messages and pull-request descriptions from a set of changes, matching the project's existing git conventions (defaulting to Conventional Commits). Use when the user has staged or finished changes and wants a commit message, is opening a PR and needs a description, or asks to "summarize this change", "write the commit", or "draft the PR". Reads the project's AGENTS.md and commit history to match its format; slots after implementation and feeds into review.
---

# Commit & PR Writer

Turn a set of changes into a clear commit message and, when needed, a PR description — derived from what actually changed and matching the project's own conventions.

## Establish the change

Get the diff to describe, in this order:
1. A provided commit range, PR, or branch.
2. Staged changes: `git diff --staged`.
3. Unstaged changes: `git diff`.
4. A diff pasted by the user.

If nothing is found, ask what to describe rather than guessing.

## Match the project's conventions first

Before writing, check how this repo actually does it — the Git/PR section of AGENTS.md and recent `git log`. If the project has an established format (a scope set, a `[project] Title` PR style, squash conventions), match it. Only fall back to the Conventional Commits default below when there's no established convention. Imposing a format the repo doesn't use is the same mistake as ignoring its code conventions.

## Commit message

Default format (Conventional Commits):

```
type(scope): short imperative summary

Optional body explaining what changed and why — not how.

Optional footer: Refs #123, BREAKING CHANGE: ...
```

- **Type** — feat, fix, docs, refactor, perf, test, build, ci, chore (or the project's set).
- **Scope** (optional) — the area touched, e.g. `auth`, `checkout`.
- **Summary** — imperative mood ("add", not "added"), lowercase, no trailing period, ~50 chars.
- **Body** (when the change isn't self-evident) — wrap ~72 chars and explain the reason; the diff already shows the what.
- **Breaking change** — add `!` after the type/scope and a `BREAKING CHANGE:` footer.

Two rules that matter more than the format:
- **Derive, don't fabricate.** Describe only what's in the diff. The *what* comes from the code; the *why* often doesn't — if the rationale isn't inferable, ask rather than invent one.
- **One concern per commit.** If the diff mixes unrelated changes, say so and propose splitting it into atomic commits instead of writing one vague message that papers over all of them.

## PR description

When opening a PR, draft this — omit empty sections and keep it scannable:

- **Title** — the squash-commit summary, in the project's PR title style.
- **What & why** — a sentence or two on the change and its motivation.
- **Changes** — the notable changes at a high level, not a file-by-file dump.
- **Testing** — how it was verified; note manual steps, and screenshots for UI changes.
- **Breaking changes / migration** — only if applicable.
- **Linked issues** — e.g. `Closes #123`.
