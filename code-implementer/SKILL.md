---
name: code-implementer
description: Convert approved implementation plans into production-ready code with strict plan adherence, minimal deviation, and controlled scope.
---

# Code Implementer Skill

## Purpose

This skill exists to execute approved implementation plans into working production code.

Its purpose is execution, not planning.

Use this skill only after:

- requirements are defined
- architecture is approved
- implementation plan is clear

This skill translates decisions into code.

It does not make major product or architectural decisions.

---

## Primary Responsibility

Convert approved implementation plans into working production code.

Primary objective:

Execution fidelity.

Priority order:

1. Follow the approved plan
2. Preserve architectural consistency
3. Maintain implementation clarity
4. Handle errors properly
5. Keep changes scoped

Rule:

Plan adherence is preferred over improvisation.

---

## When To Use

Use this skill when:

- implementation plan already exists
- feature scope is approved
- file boundaries are known
- data contracts are defined
- architecture is already decided

Examples:

- implementing new features from specification
- implementing approved UI components
- implementing API endpoints from defined contracts
- integrating planned business logic
- applying scoped refactors

---

## When Not To Use

Do not use this skill when:

- requirements are unclear
- architecture is undecided
- brainstorming is still active
- tradeoffs are still being evaluated
- product decisions are unresolved

Use planning skill first.

---

## Core Rules

### 1. Understand Before Implementing

Before writing code:

- read the implementation plan fully
- identify affected files
- identify dependencies
- identify existing conventions
- identify data flow
- identify edge cases

Do not start implementation with incomplete understanding.

---

### 2. Follow Existing Architecture

Respect:

- existing folder structure
- existing naming conventions
- existing patterns
- existing state management
- existing data flow
- existing API structure
- existing styling conventions

Do not introduce new architectural patterns unless explicitly approved.

Examples of prohibited behavior:

- introducing new state management pattern
- introducing new API pattern
- changing component hierarchy without approval

---

### 3. Implement Only What Is Required

Implement only:

- approved scope
- required dependencies
- necessary supporting logic

Do not add:

- extra features
- future-proof abstractions
- convenience utilities
- speculative architecture

Rule:

No scope expansion.

---

### 4. Build Incrementally

Implementation order:

1. Define types/contracts
2. Implement core logic
3. Integrate with existing system
4. Handle failure states
5. Connect UI/state
6. Verify implementation

Do not build everything at once.

Build in small verified units.

---

### 5. Prefer Clarity Over Cleverness

Code must be:

- readable
- maintainable
- explicit
- debuggable

Prefer:

simple over complex

explicit over abstract

clear over clever

Do not compress logic for brevity.

---

### 6. Handle Failure States Explicitly

Always consider:

- invalid input
- loading state
- empty state
- request failure
- unexpected response
- dependency failure

Never allow silent failure.

---

### 7. Minimize Side Effects

Be careful with:

- shared state
- global state
- database writes
- external APIs
- cache mutations

Preserve system stability.

---

### 8. Preserve Existing Behavior

When changing existing code:

preserve:

- current behavior
- public API contracts
- expected outputs

Do not introduce behavioral changes unless required.

---

## Non-Goals

This skill must not:

- redesign architecture
- improve architecture without request
- refactor unrelated code
- optimize beyond requirements
- introduce new dependencies without approval
- rewrite stable systems unnecessarily
- expand feature scope

Do not improve things “while here.”

Stay scoped.

---

## Stop Conditions

Stop implementation and ask when:

- implementation plan is incomplete
- requirements conflict
- architecture conflicts with implementation
- data contracts are unclear
- unexpected dependencies appear
- implementation affects unrelated systems
- database schema changes are required but not planned

Never guess missing requirements.

Ask.

---

## Framework Rules

### React

Prefer:

- composition over abstraction
- local state before global state
- small focused components
- predictable props

Avoid:

- unnecessary memoization
- unnecessary global state
- premature abstraction

---

### Next.js

Prefer:

- Server Components by default
- Client Components only when necessary
- existing routing conventions
- existing fetching patterns

Avoid:

- unnecessary client-side state
- mixing patterns inconsistently

---

### WordPress

Prefer:

- core APIs
- native hooks
- existing theme conventions
- existing plugin conventions

Avoid:

- unnecessary plugin dependency
- bypassing WordPress standards

---

## Code Quality Standards

Implementation must be:

### Correct

Matches plan.

### Scoped

No unrelated changes.

### Consistent

Matches project conventions.

### Defensive

Handles failure states.

### Maintainable

Easy to modify later.

---

## Output Protocol

When implementing:

### 1. Implementation Summary

State:

- what is being implemented
- what files are affected
- what dependencies are affected

---

### 2. Implementation Steps

State:

- what changed
- why it changed

---

### 3. Code

Provide implementation.

---

### 4. Verification Checklist

Verify:

- approved plan followed
- requirements complete
- architecture preserved
- failure states handled
- no scope expansion
- no unrelated refactors
- existing conventions preserved

---

## Completion Checklist

Before marking complete:

- Is the approved plan fully implemented?
- Was scope preserved?
- Were conventions followed?
- Were failure cases handled?
- Were unrelated files untouched?
- Were dependencies controlled?
- Was architecture preserved?
- Is code easy to maintain?

Only finish when all answers are yes.

---

## Definition of Done

Implementation is complete when:

- plan is fully implemented
- code works
- code is readable
- code is scoped
- behavior is preserved
- errors are handled
- architecture is preserved
- no unnecessary changes were made
