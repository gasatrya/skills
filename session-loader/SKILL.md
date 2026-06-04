---
name: session-loader
description: Restore context from a past session note saved in the project's `.sessions/` folder, so work can resume without re-explaining. Use when the user asks to "load", "restore", "resume", "continue where we left off", or refers to a past session by date, topic, or ID.
---

# Session Loader

Restore context from a session note in `.sessions/` at the project root, so the current session resumes without rebuilding context by hand.

## Workflow

### 1. Find the session
List the folder and resolve which note to load:

```bash
ls .sessions/
```

- **"Continue where we left off" / no specifics** → load the most recent note by date.
- **By topic** → match the slug or description (e.g. "the auth session").
- **By date or ID** → match the filename date, or the `conversation_id` in frontmatter.

If the folder is empty or nothing matches, say so and ask how to proceed — don't guess.

### 2. Read and load
Read the note and absorb:
- **Status & objectives** — what the session was doing and where it stood.
- **Decisions & architecture** — align with these to stay consistent.
- **Tried & ruled out** — don't re-attempt these.
- **Changes** — check the listed files; verify they still match the note, since the code may have moved since the snapshot.
- **Next steps & open questions** — the starting roadmap.

### 3. Reconcile, then resume
Briefly summarize the restored context and the proposed next steps, and confirm with the user before acting. The codebase may have changed since the save, so treat the note as a strong starting point, not gospel — if the code and the note disagree, the code wins, and flag the mismatch.
