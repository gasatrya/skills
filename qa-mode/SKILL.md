---
name: qa-mode
description: Use this skill to design test plans, write automated test scripts, and perform root cause analysis on bugs.
---

# QA Engineering Workflow

## 1. Test Strategy (The 80/20 Rule)
Prioritize testing based on impact and risk.
- **Critical Path**: Identify the "Happy Path" (the core user journey).
- **Edge Cases**: Identify boundary conditions (e.g., empty states, max limits, invalid inputs).
- **Regression**: Identify high-risk areas touched by recent code changes.

## 2. Test Design & Scripting
When creating tests (Unit, Integration, or E2E):
- **Isolation**: Ensure tests do not depend on other tests.
- **Idempotency**: Tests must produce the same result every time they run.
- **Cleanup**: Always include a teardown step to reset the environment state.
- **Readability**: Use descriptive names (e.g., `should_fail_when_password_is_too_short`).

## 3. Bug Reporting & RCA
When a bug is discovered, follow the "Five Whys" for Root Cause Analysis (RCA):
- **Reproduce**: Provide a minimal, clear set of steps to trigger the bug.
- **Expected vs. Actual**: Clearly state the discrepancy.
- **Environment**: Note the OS, browser, or hardware version.
- **Log Collection**: Attach relevant logs, stack traces, or network payloads.

## 4. Automation Maintenance
- **Flakiness Audit**: Identify and quarantine tests that fail inconsistently.
- **Performance**: Monitor test suite execution time; optimize slow setups.
- **Coverage**: Use tools to ensure critical logic is exercised, but prioritize meaningful assertions over 100% line coverage.

## 5. Definition of Done
A task is "QA Complete" only when:
- All critical paths are verified.
- Automated tests are integrated into the CI/CD pipeline.
- Documentation for the new test cases is updated.
