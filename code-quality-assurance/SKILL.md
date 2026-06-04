---
name: code-quality-assurance
description: Deep architectural audits, root-cause investigation of complex or intermittent bugs, and production-readiness hardening — across any language or framework. Use this when the user reports a tricky, flaky, or hard-to-reproduce bug, asks why something is unstable or slow, needs assurance that a feature is production-ready, or wants a deep audit of state, data integrity, concurrency, or hot-path performance. For routine review of a specific diff or PR before merge, use a dedicated code-review skill instead.
---

# Code Quality Assurance

Operate as a senior QA engineer. The goal isn't just to make a bug go away — it's to protect system integrity, performance, and long-term stability by finding *why* a failure was possible, not only where it surfaced.

These principles are language- and framework-agnostic; apply them to whatever stack the code is in. The stack-specific tells at the end are a starting point for how each principle tends to show up, not the limit of where the skill applies.

## Core mindset

**Patterns over patches.** When you find a bug, name the architectural pattern that allowed it and fix *that*, so the whole class of bug can't recur. A patch that leaves the enabling pattern in place is incomplete.

**Defensive rigor.** Assume state can be corrupted, I/O can fail, and race conditions will happen. Put guards where the failure would actually land, not where it's convenient.

**Behavioral integrity.** In apps that demand sustained user focus, the UI must never mislead the user or break their flow — confidently-wrong state is worse than a visible, honest error.

## Establish the target

Before auditing, pin down what you're looking at and what "correct" means:
- Get the code or feature in scope and the actual concern — a bug report, a performance complaint, or a production-readiness check.
- Identify the **source of truth** for the relevant state: is it single and authoritative, or duplicated/derived in ways that can diverge?
- If the scope or expected behavior is unclear, ask before digging. Auditing the wrong thing is wasted effort.

## Investigate

**Map the system.**
- *Source of truth:* is each piece of state owned in one place and updated atomically?
- *Blast radius:* if this line or call fails, what else breaks — cascading UI failures, divergent persisted data, stuck async state?
- *Hot-path cost:* for code on ticks, intervals, rapid events, or every request, measure the real cost (compute, I/O, re-renders, queries) — not just correctness.

**Reproduce before fixing.**
- Write a failing test or small script that triggers the failure; reason it through only when it genuinely can't be run.
- Pin the exact race window, edge case, or input that causes it.
- State the worst-case consequence (data loss? silent corruption? frozen UI?) — that calibrates the fix's priority.

## Hardening checklist (language-agnostic)

A fix is complete only when:
- **Atomic state** — mutations to shared or persisted state are atomic and free of read-modify-write races (functional updates, transactions, locks, or compare-and-swap, whatever the stack offers).
- **I/O & failure resilience** — every fallible operation (network, disk, DB, external API) handles failure explicitly and surfaces it; nothing is swallowed silently.
- **Boundary validation & contracts** — data is validated or typed at the boundaries it crosses; types or runtime checks model the real states, including loading, empty, error, and partial.
- **Hot-path performance** — repeated or high-frequency work is measured, then cached, batched, debounced, or eliminated.
- **Pattern fixed** — the architectural cause is addressed, not just this one instance.

## Report format

Present findings highest-severity first. For each issue:
- **Location & severity** — Critical (data loss/corruption or crash), Major (broken behavior or race condition), or Minor (performance or robustness gap).
- **Root cause** — the pattern that allowed it, not just the symptom.
- **Reproduction** — the test/script or the exact conditions that trigger it.
- **Fix** — the concrete change, plus the guard that prevents the whole class from recurring.

## Stack-specific tells

Non-exhaustive examples of how the principles above surface in common stacks. Add or extend as needed — if this section grows, move each stack into its own `references/<stack>.md` file so the core stays lean.

**JavaScript / TypeScript (React, Next.js, TanStack Start)**
- *Atomic state:* functional state updates; watch for stale closures over state inside async callbacks, intervals, or effects.
- *Races:* effects firing out of order, missing cleanup, in-flight requests not cancelled on unmount or refetch.
- *I/O:* every promise/await has rejection handling; errors surface to the UI, not just the console.
- *Contracts:* no `any`; validate external data (API responses, localStorage) at the edge; model loading/empty/error explicitly.
- *Performance:* re-render and main-thread cost of tick/interval logic; debounce/throttle/memoize; correct server-vs-client component boundaries; server-state caching (e.g. TanStack Query) over ad-hoc fetching.

**WordPress / PHP**
- *Atomic state:* option/transient read-modify-write races; prefer atomic updates and real DB transactions; enforce nonce + capability checks on writes.
- *I/O:* check return values of `wp_remote_*`, DB, and filesystem calls; handle `WP_Error`; never assume success.
- *Contracts:* sanitize and validate input on the way in, escape output on the way out; declare types where the PHP version allows; avoid leaning on `mixed`.
- *Performance:* N+1 queries and unbounded `WP_Query`; missing object cache or transients; expensive work running on every request or in frequently-fired hooks.
