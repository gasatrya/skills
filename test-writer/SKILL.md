---
name: test-writer
description: Write focused, behavior-driven tests for new or existing code — unit, integration, or end-to-end — matching the project's existing test setup and conventions. Use when the user asks to write or add tests, wants coverage for a feature or bug fix, asks "how should I test this", or has just implemented something that needs verification. Defaults to the project's framework (e.g. Vitest + React Testing Library, Playwright, PHPUnit); pairs with the planner's validation strategy and the QA skill's coverage checks.
---

# Test Writer

Write tests that verify behavior and would actually catch a regression — not tests that mirror the implementation and break on every refactor.

## The principle: test behavior, not implementation

Test what the code does from the perspective of its caller or user, not how it does it internally. A good test survives a refactor that preserves behavior and fails when behavior breaks. Concretely:
- Assert on observable outputs and effects, not on internal state, private methods, or structure.
- For UI, interact the way a user would — roles, labels, visible text — rather than reaching into component internals or test IDs.
- A test that can't fail is worthless; make sure each test would fail if the behavior it checks regressed.
- Don't test the framework or third-party libraries — test your code.

## What to test (priority order)

1. **The contract** — the main behavior the code promises, happy path first.
2. **Edge cases** — boundaries, empty inputs, large inputs, the off-by-one zone.
3. **Error paths** — invalid input, failed I/O, rejected promises; the states the QA skill cares about (loading, empty, error).
4. **Regressions** — when fixing a bug, write the test that reproduces it first, then make it pass.

Cover behavior that matters and is likely to break. Don't chase a coverage percentage — a high number full of implementation-coupled tests is worse than fewer meaningful ones.

## Match the project first

Check AGENTS.md and the existing tests for the framework, where tests live, the naming style, and how to run a single test. Match that setup rather than introducing a new framework or pattern.

## Structure

- **Name by behavior** — "returns empty list when nothing matches", not "test getList".
- **Arrange–Act–Assert** — set up, do the thing, assert; keep the three visually distinct.
- **One concern per test** — a focused failure tells you exactly what broke.
- **Independent tests** — no shared mutable state or order dependence between them.
- **Mock only at boundaries** — network, time, randomness, external services. Over-mocking tests the mocks, not the code.

## Pick the level

Favor fast, focused tests; reserve slow ones for what truly needs them.
- **Unit** — pure logic, transformations, edge-case-heavy functions.
- **Integration** — units working together; the best ROI for React UI is rendering the component, interacting, and asserting on what the user sees.
- **End-to-end** — only critical user journeys, kept few because they're slow and brittle.

## Stack-specific patterns

Non-exhaustive tells for common stacks; extend or move to `references/<framework>.md` if this grows.

**Vitest + React Testing Library** — query by accessible role/label/text (`getByRole`); drive interaction with `userEvent`, not `fireEvent`; use `findBy*` for async UI; mock network with MSW rather than stubbing `fetch` ad hoc; avoid snapshot tests except for stable, intentional output.

**Playwright (E2E)** — role-based locators; rely on web-first auto-waiting assertions instead of manual sleeps; isolate state with fixtures and per-test setup/teardown; keep the suite to high-value journeys (auth, checkout, the core flow).

**PHPUnit (WordPress)** — build fixtures with WP factories; assert hook and filter behavior rather than internals; never hit external services; use data providers for case tables; reset global and option state between tests.
