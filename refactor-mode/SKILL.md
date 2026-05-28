---
name: refactor-mode
description: Proactively use this skill to analyze and improve code structure, maintainability, and performance through systematic refactoring techniques.
---

Improve code quality through systematic analysis and transformation techniques.

## When to Use

- User requests code refactoring or improvement
- Code reviews indicate technical debt
- Need to apply design patterns or best practices
- When user says "refactor", "clean up", "improve this code", "apply patterns"
- Code smells detected (long functions, duplication, etc.)

## Core Responsibilities

1. **Code Analysis**: Examine code structure, complexity, and identify issues
2. **Refactoring**: Apply transformations to improve maintainability
3. **Pattern Application**: Identify and apply appropriate design patterns
4. **Verification**: Ensure refactored code maintains functionality
5. **Documentation**: Explain changes made and rationale

## Refactoring Process

1. **Understand Context**: Read the code and understand its purpose
2. **Identify Issues**: Detect code smells and improvement opportunities
3. **Plan Changes**: Determine appropriate refactoring techniques
4. **Apply Refactoring**: Transform code while preserving behavior
5. **Verify**: Ensure tests pass and functionality is maintained
6. **Document**: Explain what was changed and why

## Common Refactoring Patterns

**Extract Method**: Break down long functions
**Extract Class**: Separate concerns into focused classes
**Rename**: Improve variable/function names for clarity
**Replace Magic Numbers**: Use named constants
**Eliminate Duplication**: Extract common code
**Simplify Conditionals**: Reduce nested logic
**Introduce Parameter Object**: Group related parameters
**Replace Conditional with Polymorphism**: Use OOP patterns

## Output Format

```
## Refactoring Analysis

**Original Code**:
```python
[code snippet]
```

**Issues Identified**:
- Issue 1: [Description]
- Issue 2: [Description]

**Refactoring Applied**:
1. [Refactoring technique 1]
2. [Refactoring technique 2]

**Refactored Code**:
```python
[improved code]
```

**Changes Summary**:
- [Metric]: [Before] → [After]
- Lines of code: [Before] → [After]
- Cyclomatic complexity: [Before] → [After]

**Rationale**:
[Explanation of why these changes improve the code]

**Testing Recommendations**:
- [ ] Add unit tests for [function]
- [ ] Verify [behavior]
- [ ] Check [edge case]
```

## Best Practices

- **Preserve Functionality**: Refactoring must not change behavior
- **Small Steps**: Apply one refactoring at a time
- **Test Continuously**: Run tests after each change
- **Use Tools**: Leverage linters, formatters, and analyzers
- **Explain Rationale**: Document why each change improves code
- **Consider Context**: Match team conventions and project style

## What This Skill Does NOT Do

- Generate new code from scratch (use coding skill)
- Make architectural decisions (use architect skill)
- Optimize performance beyond readability (use performance skill)
- Write tests (use testing skill)
