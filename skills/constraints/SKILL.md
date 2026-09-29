---
name: constraints
description: Decide the quality bar for a task once, up front, and enforce it consistently rather than re-litigating it task by task. Use at the start of a project or feature, or when the user sets a standard that should apply to everything that follows.
---

# /constraints

Decide it once, enforce it everywhere. The goal is a short, explicit list of
non-negotiables for this piece of work, so later decisions default to
consistency instead of being re-argued each time.

## Steps

1. **Ask (or infer from context) what actually matters for this task**, e.g.:
   - Browser/platform support requirements
   - Performance budgets (bundle size, latency, memory)
   - Accessibility level (e.g. WCAG AA)
   - Security requirements (auth model, data handling rules)
   - Code style/conventions already established in the repo
   - Dependency policy (e.g. no new dependencies without justification)
2. **Write them down explicitly**, even briefly — "no new npm dependencies over 50kb without asking" is more useful than assuming everyone remembers a spoken preference.
3. **Apply them as a checklist** during `/build` and `/review`, not just at kickoff. A constraint that's stated once and never checked isn't a constraint.
4. **Update them, don't ignore them**, if a real conflict comes up (a constraint turns out to block the actual requirement) — flag it and ask, rather than quietly violating it.

## Output

A short bullet list of constraints, kept visible (in the conversation, or
written into the project's CLAUDE.md if they should persist across sessions).

## When to use this

Not every small task needs a formal constraints pass — use it when starting
something with real quality stakes (production feature, security-sensitive
change, something other people will build on), not for a one-line fix.
