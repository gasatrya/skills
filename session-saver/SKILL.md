---
name: session-saver
description: Summarize the current working session and save it as a Markdown note in the project's `.sessions/` folder, so a future session can resume without re-deriving context. Use at the end of a work session, when the user asks to "save", "snapshot", "checkpoint", or "remember where we are", or before a likely context reset.
---

# Session Saver

Capture the current session as a concise Markdown note in `.sessions/` at the project root, so a later session — or a fresh agent — can resume quickly without rebuilding context from scratch. Optimize for fast reload, not completeness: record decisions, current state, and what's next, not a transcript.

## Workflow

### 1. Gather metadata
- **Date** — today, `YYYY-MM-DD`.
- **Slug** — a few words naming the task (e.g. `auth-refactor`).
- **Conversation ID** — if the environment exposes one, record it in frontmatter as a secondary reference; don't rely on it as the filename.

### 2. Choose the filename
Use `YYYY-MM-DD-slug.md` (same convention as `.specs/`). If you already saved this session earlier, update that same file in place rather than creating a duplicate — match it by the `conversation_id` in frontmatter, or by the file you wrote earlier this session.

### 3. Write the note
Use this template, omitting any section that's genuinely empty and keeping entries terse:

```markdown
---
date: YYYY-MM-DD
slug: <slug>
conversation_id: <id-if-available>
status: in-progress | done | blocked
---

# Session: <short description>

## Status
One line on where things stand right now.

## Objectives
What this session set out to do.

## Decisions & architecture
Key decisions, patterns, constraints, and trade-offs agreed on — and the *why*, briefly.

## Changes
Files touched and what changed in each:
- `relative/path/to/file.tsx` — what changed and why.

## Tried & ruled out
Approaches attempted that didn't work, and why — so they aren't re-attempted next time.

## Open questions / blockers
Anything awaiting a decision or external input.

## Next steps
Concrete pending tasks, in priority order.
```

### 4. Save
Write the note to `.sessions/YYYY-MM-DD-slug.md` in the project root, creating the `.sessions/` folder if it doesn't exist. Confirm the saved path to the user.
