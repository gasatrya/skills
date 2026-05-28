---
name: research-mode
description: Use this skill to find the latest documentation, best practices, and real-world code patterns for any technology or framework.
---

Gather comprehensive information on technical topics from authoritative sources.

## When to Use

- Finding official documentation for a technology
- Researching best practices for a pattern or approach
- Looking up real-world code examples
- Understanding latest trends or updates
- Comparing different solutions or libraries
- Gathering resources for decision-making
- When user says "do a research" or "run a research"

## Core Responsibilities

1. **Understand Request**: Identify the specific topic, technology, or problem
2. **Gather Sources**: Find official docs, tutorials, blogs, and code examples
3. **Evaluate Quality**: Prioritize authoritative, up-to-date sources
4. **Synthesize Findings**: Summarize key insights with actionable information
5. **Provide Resources**: Include links for further reading

## Tool Guidelines

- Use `gh_grep` to locate real-world code examples or patterns from GitHub
- Use `ctx7` cli command to find official documentation faster. Run `npx ctx7 --help` for options. 

## Research Methodology

1. **Identify Core Topic**: What technology, pattern, or problem?
2. **Search Broadly**: Start with official documentation and docs
3. **Find Examples**: Look for real-world implementations
4. **Verify Currency**: Check dates, versions, and last updates
5. **Organize Results**: Group by category (docs, examples, patterns)

## Source Priority

| Priority | Source Type |
|----------|-------------|
| 1st | Official documentation |
| 2nd | Official tutorials/guides |
| 3rd | Reputable blogs (conf.dev, medium popular) |
| 4th | GitHub examples (official repos) |
| 5th | Stack Overflow/community answers |

## Output Format

```
## Research Summary

**Topic**: [Brief description]
**Key Findings**:
- Finding 1
- Finding 2
- Finding 3

---

### Official Documentation

- [Title](url) - Description
- [Title](url) - Description

### Best Practices

- Practice 1 with explanation
- Practice 2 with explanation

### Code Examples

```language
// Concise example with comments
code snippet
```

### Additional Resources

- [Title](url) - Description
```

## Quality Standards

- **Accuracy**: Verify information across sources
- **Recency**: Prefer recent documentation (check dates)
- **Actionability**: Include practical examples
- **Clarity**: Explain concepts clearly for the context
- **Completeness**: Cover main aspects of the topic

## Handling Ambiguity

If the request is too broad or unclear:
- Ask for clarification on the specific use case
- Suggest narrowing the scope
- Propose alternative approaches
