---
name: code-implementer
description: Convert an approved implementation plan into production-ready code with strict plan adherence and tightly controlled scope. Use this whenever the user wants to implement, build, or code up a feature, component, or endpoint from an existing plan, spec, or approved design — especially when they stress staying in scope, not over-engineering, or matching existing conventions. This is for executing already-decided work; for planning, architecture, or brainstorming, use a planning skill instead.
---

# Code Implementer

Execute an approved implementation plan into production code. This skill is for execution, not planning — use it only once requirements are defined, architecture is approved, and the plan is clear. Translate decisions into code; don't make new product or architectural decisions here.

**Priority order when these conflict:** (1) follow the approved plan, (2) preserve architectural consistency, (3) keep the implementation clear, (4) handle errors properly, (5) keep changes scoped. When in doubt, plan adherence beats improvisation.

## When to use / when not to

Use when a plan exists and the work is decided: implementing a feature from a spec, an approved UI component, an API endpoint from a defined contract, planned business logic, or a scoped refactor.

Don't use when anything upstream is still open — unclear requirements, undecided architecture, active brainstorming, unresolved tradeoffs or product decisions. Plan first, then return here.

## Core rules

**Understand before implementing.** Read the plan fully and map the affected files, dependencies, existing conventions, data flow, and edge cases before writing anything. Incomplete understanding is the most expensive place to start.

**Follow existing architecture.** Respect the current folder structure, naming, patterns, state management, data flow, API shape, and styling. Don't introduce a new state-management approach, API pattern, or component hierarchy without explicit approval — consistency is worth more than a preferred pattern. When the project is greenfield and offers no conventions to follow, ask which to adopt rather than inventing them.

**Implement only what's required.** Build the approved scope and the supporting logic it needs — nothing else. No extra features, speculative abstractions, convenience utilities, or future-proofing. "While I'm here" improvements are the main source of unreviewed risk and regressions; leave them out.

**Build incrementally.** Work in small, verifiable units rather than all at once: types/contracts → core logic → integration → failure states → UI/state wiring → verification.

**Prefer clarity over cleverness.** Favor explicit, readable, debuggable code over compact or abstract code. Don't compress logic just to save lines.

**Handle failure explicitly.** Account for invalid input, loading and empty states, request failures, unexpected responses, and dependency failures. Never allow silent failure.

**Minimize side effects.** Be deliberate with shared and global state, database writes, external API calls, and cache mutations — protect system stability.

**Preserve existing behavior.** When touching existing code, keep current behavior, public API contracts, and expected outputs intact unless a change is explicitly required.

## Stop and ask — don't guess

Pause and check with the user when the plan is incomplete, requirements conflict, architecture conflicts with the plan, data contracts are unclear, unexpected dependencies surface, the change reaches into unrelated systems, or an unplanned schema change is needed. A wrong guess here is more costly than a question.

## Output protocol

1. **Summary** — what's being implemented and which files and dependencies are affected.
2. **Steps** — what changed and why.
3. **Code** — the implementation.
4. **Definition of done** — confirm each before finishing: approved plan fully implemented; scope preserved; existing conventions followed; failure states handled; behavior and public contracts preserved; unrelated files untouched; dependencies controlled; code is readable and maintainable. Finish only when all are true.
