---
name: bug-debugging
description: Use this skill when the user reports a bug, asks to debug or investigate broken behavior, or wants to check why something isn't working. Triggers include "debug", "fix this bug", "why isn't this working", "this is broken", "investigate this error", or pasting a stack trace / error message. Use for diagnosing and fixing defects in existing code.
---

# Bug Debugging

## Core principle
Diagnose before changing. Never guess-and-replace code. Confirm with the user before any action that could lose work, change behavior broadly, or rest on an unverified assumption.

## Workflow

1. **Reproduce / locate**
   - Identify the exact symptom, expected vs. actual behavior, and how to trigger it.
   - If you cannot reproduce or the repro steps are unclear, ASK before proceeding.

2. **Gather context**
   - Read the relevant code, logs, and stack trace. Trace the failure to its source, not just where it surfaces.
   - If key files, versions, env, or inputs are unknown, ASK rather than assume.

3. **Form a hypothesis**
   - State the suspected root cause in one or two sentences.
   - Note your confidence level. If low, say so.

4. **Confirm before acting** (mandatory)
   Ask the user before you:
   - Modify, delete, or overwrite files
   - Change behavior beyond the reported bug (refactors, dependency bumps, API changes)
   - Run destructive or stateful commands (migrations, resets, deploys, `rm`, force-push)
   - Proceed on an assumption you couldn't verify
   - Choose between multiple viable fixes

   Phrase it as a clear question with options, e.g.:
   > "Root cause looks like X. I can fix it by either (a) ... or (b) .... Which do you prefer?"

5. **Apply the fix**
   - Make the smallest change that resolves the root cause.
   - Explain what you changed and why.

6. **Verify**
   - Re-test the original symptom. Confirm no obvious regressions.
   - If you can't verify, tell the user what they should check.

## Rules
- When uncertain, ASK — don't assume.
- One root cause at a time; don't bundle unrelated fixes.
- Surface trade-offs and let the user decide on anything ambiguous or risky.
