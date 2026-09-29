---
name: minimal-implementation
description: Push an implementation toward the simplest solution that actually works — fewer unnecessary abstractions, native/stdlib features first, YAGNI. Use before or during writing code, whenever a task risks over-building (new dependency, new component, new abstraction layer, new config option).
---

# Minimal implementation

Custom, in-house version of the same idea behind third-party "lazy senior dev"
style tools — written locally so it's fully auditable, with no external
dependency or code execution.

## The ladder

Before adding anything new, check it against this list in order and stop at the
first rung that holds:

1. **Does this need to exist?** If the task doesn't actually require it, skip it (YAGNI).
2. **Already in this codebase?** Reuse the existing function/component/pattern instead of writing a new one.
3. **Does the standard library do it?** Use that instead of a new dependency.
4. **Native platform/language feature?** Use that instead of a library (e.g. `<input type="date">` instead of a date-picker package).
5. **Already-installed dependency does it?** Use that instead of adding a new one.
6. **Can it be done in one line?** Do it in one line.
7. **Only then:** write the minimum new code that works.

Run this check *after* understanding the actual problem and reading the code the
change touches — the ladder picks the simplest rung for a well-understood
problem, it doesn't replace understanding the problem.

## What this does NOT mean

Lazy about the solution, never about safety. These are never cut for brevity:

- Validation at trust boundaries (user input, external APIs, file uploads)
- Error handling for real failure modes
- Data-loss prevention (confirmations before destructive actions, backups)
- Security (auth checks, injection prevention, secret handling)
- Accessibility (semantic HTML, keyboard nav, ARIA where needed)

If a "simpler" version would drop one of these, it isn't actually simpler — it's
moving the missing complexity onto whoever hits the bug later.

## Applying it

When a task involves adding something (a component, a dependency, a config
option, a helper function), walk the ladder explicitly before writing code.
When reviewing a diff, check whether anything added skipped a rung it shouldn't
have (e.g. a new dependency for something the stdlib already does).

Related: see the "Code simplicity" section in `~/.claude/CLAUDE.md` for the
always-on summary of this same checklist. For a full pass over *already written*
code (not what to write next, but cleaning up what exists), use the `/simplify`
skill instead — that one looks for reuse/simplification/efficiency issues in a
diff, this one is applied while deciding what to write in the first place.
