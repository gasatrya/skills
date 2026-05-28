---
name: spec-mode
description: Use this workflow for multi-step implementation, multi-file changes, bug investigations, or architectural decisions to ensure planning before coding.
---

# Specification Mode Workflow

## Purpose

This skill exists to create implementation specifications before coding begins.

Its purpose is to reduce implementation mistakes by improving clarity, identifying constraints, and defining execution boundaries.

This skill is for thinking, not coding.

Primary goal:

Turn unclear work into an approved implementation plan.

Rule:

No code changes before approval.

---

## When to Activate

Use this workflow when:

- planning a new feature
- implementing multi-step features
- modifying 2 or more files
- fixing bugs that require investigation
- changing architecture or core system behavior
- working in unfamiliar codebases
- working on security-sensitive systems
- changing data contracts
- changing API behavior
- changing database behavior

Use this workflow when uncertainty exists.

If implementation affects multiple system boundaries, activate spec-mode.

---

## When Not to Activate

Do not use this workflow when:

- fixing obvious typos
- changing isolated UI text
- making small isolated code changes
- making non-structural styling changes
- making trivial updates with no system impact

Use direct implementation for low-risk isolated changes.

---

# Phase 1: Analysis (Read-Only)

Conduct a full read-only investigation.

No file modifications.

No implementation.

No speculative coding.

Goal:

Understand the system before planning.

---

## Analysis Checklist

### Context Discovery

Identify:

- affected systems
- existing architecture
- related components
- data flow
- external dependencies

Questions:

- what currently exists?
- what already solves part of this?
- what depends on this?

---

### Pattern Discovery

Identify:

- codebase patterns
- naming conventions
- file organization
- framework conventions
- architectural style

Follow existing patterns unless change is intentional.

---

### Constraint Discovery

Identify:

- technical constraints
- framework constraints
- business constraints
- backward compatibility requirements
- performance requirements
- security requirements

Questions:

- what cannot change?
- what must remain compatible?
- what limitations exist?

---

### Risk Discovery

Identify:

- possible regressions
- side effects
- dependency risks
- integration risks
- data risks

Questions:

- what could break?
- what systems depend on this?
- what hidden impact exists?

---

### Standards Review

Consult:

- AGENTS.md
- project conventions
- existing implementation patterns

Respect project standards.

---

# Phase 2: Specification Generation

Create a full implementation plan.

This plan should be detailed enough for direct implementation.

The plan must reduce ambiguity.

---

## Required Specification Sections

### 1. Problem Definition

Define:

- what problem exists
- why it matters
- what needs to change

Be specific.

---

### 2. Acceptance Criteria

Define:

What must be true for this to be considered done?

Include:

- expected behavior
- expected outputs
- expected system state

Acceptance criteria must be testable.

---

### 3. Technical Strategy

Define:

- chosen implementation strategy
- chosen patterns
- chosen architecture decisions
- chosen dependencies

Explain:

Why this approach?

---

### 4. Constraints

Define:

- technical constraints
- compatibility requirements
- system limitations
- non-negotiable boundaries

Make constraints explicit.

---

### 5. Risk Assessment

Define:

- possible regressions
- affected systems
- failure points
- rollback considerations

State mitigation strategy.

---

### 6. File-by-File Breakdown

List:

- files to create
- files to modify
- files to remove

For each file:

- what changes
- why it changes

Make scope explicit.

---

### 7. Data Flow Impact

If relevant:

Define:

- input changes
- output changes
- API changes
- state changes
- database changes

Clarify data movement.

---

### 8. Validation Strategy

Define:

What should be tested?

How should it be tested?

What should the expected result be?

Include:

- functional verification
- edge case verification
- regression verification

Commands are optional.

Validation logic is required.

---

# Phase 3: Review & Approval

Present the complete specification.

Do not implement.

Do not edit files.

Wait for explicit approval.

Approval must be clear.

Examples:

Approved:
- approved
- proceed
- implement
- looks good

Not approved:
- maybe
- looks okay
- thinking about it

Do not assume approval.

---

## Revision Loop

If feedback is given:

- revise the specification
- preserve approved parts
- update affected sections
- resubmit for approval

Repeat until approved.

---

# Phase 4: Handoff

After approval:

handoff implementation to execution workflow.

Use implementation skill.

The approved specification becomes the implementation source of truth.

Implementation must follow the approved plan.

No redesign during implementation.

No scope expansion.

---

## Handoff Rules

Implementation workflow must:

- follow approved file plan
- preserve approved scope
- preserve architecture decisions
- preserve constraints
- preserve risk boundaries

Specification controls implementation.

---

# Phase 5: Archival

Save approved specifications to:

.specs/

Naming format:

YYYY-MM-DD-slug.md

Examples:

2026-05-07-user-auth-refactor.md

2026-05-07-checkout-validation-fix.md

Archive completed specifications.

Do not delete them.

Specs are decision history.

They help with:

- future maintenance
- regression debugging
- architectural history
- onboarding context

---

## Spec Quality Checklist

Before approval, verify:

- problem is clear
- scope is clear
- constraints are clear
- risks are identified
- affected files are listed
- acceptance criteria are testable
- validation strategy is clear
- implementation path is realistic

Only approve complete specs.

---

## Definition of Done

Specification is complete when:

- the problem is clearly defined
- implementation path is clear
- scope is bounded
- risks are identified
- constraints are documented
- affected files are identified
- validation strategy exists
- user explicitly approves
