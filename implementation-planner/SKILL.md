---
name: implementation-planner
description: Investigate and write an approved implementation plan (a "spec") before any code is written. Use this whenever work is non-trivial — multi-step features, changes spanning two or more files, bug investigations, architectural/API/data-contract/database changes, security-sensitive work, or anything in an unfamiliar codebase. Skip it for trivial isolated changes (typos, UI text, small non-structural tweaks) and implement those directly. Once a spec is approved, hand off to the code-implementer skill to build it.
---

# Implementation Planner

Turn unclear work into an approved implementation plan before coding starts. This skill is for thinking, not coding — its job is to reduce mistakes by surfacing constraints, risks, and scope up front. No code changes until the plan is approved.

## When to use

Use when there's uncertainty or system impact: planning a feature, multi-step or multi-file work, bug investigation, architecture/API/data-contract/database changes, security-sensitive systems, or unfamiliar codebases.

Skip it for trivial, isolated, low-risk changes — typos, UI text, small non-structural styling — and implement those directly.

## Phase 1 — Analyze (read-only)

Understand the system before planning anything. No file edits, no speculative code. Investigate along four lenses:

- **Context** — affected systems, existing architecture, related components, data flow, dependencies. What already exists, and what depends on this?
- **Patterns** — codebase conventions, naming, file organization, framework and architectural style. Follow them unless a change is deliberate.
- **Constraints** — technical, framework, business, backward-compatibility, performance, security. What can't change, and what must stay compatible?
- **Risk** — possible regressions, side effects, integration and data risks. What could break, and what hidden impact exists?

Also consult project standards (AGENTS.md, existing patterns) and respect them.

## Phase 2 — Write the spec

Produce a plan detailed enough to implement directly, with these sections:

1. **Problem** — what's wrong, why it matters, what must change.
2. **Acceptance criteria** — testable conditions for "done": expected behavior, outputs, and end state.
3. **Technical strategy** — chosen approach, patterns, and dependencies, plus *why* this over the alternatives.
4. **Constraints** — technical limits, compatibility requirements, non-negotiable boundaries.
5. **Risk & rollback** — likely regressions, affected systems, failure points, and the mitigation/rollback plan.
6. **File-by-file breakdown** — files to create, modify, or remove, and what changes in each and why. This is what bounds scope.
7. **Data-flow impact** (if relevant) — changes to inputs, outputs, API, state, or database.
8. **Validation strategy** — what to test and the expected results: functional, edge-case, and regression checks. Concrete commands are optional; the validation logic is required.

## Phase 3 — Review & approval

Present the complete spec and stop — no implementation, no file edits — until the user explicitly approves. Treat clear go-aheads ("approved," "proceed," "implement," "looks good") as approval, and hedges ("maybe," "looks okay," "thinking about it") as not approved. Never assume approval.

If feedback comes in, revise the affected sections, preserve what was already approved, and resubmit. Repeat until approved.

## Phase 4 — Handoff & archive

On approval, hand the spec to the **code-implementer** skill as the source of truth; implementation follows the plan without redesign or scope expansion.

Archive the approved spec to `.specs/`, named `YYYY-MM-DD-slug.md` (e.g. `2026-05-07-user-auth-refactor.md`). Never delete specs — they're decision history for future maintenance, regression debugging, and onboarding.

## Definition of done

The spec is complete when the problem, scope, constraints, and risks are clear; affected files are listed; acceptance criteria are testable; a validation strategy exists; the implementation path is realistic; and the user has explicitly approved.
