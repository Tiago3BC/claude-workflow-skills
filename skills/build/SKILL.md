---
name: build
description: Implement a plan's tasks one at a time, each one tested and reviewable in isolation. Use after /plan, when actually writing the code for an approved task list.
---

# /build

One slice at a time. The goal is that at every point during implementation,
there's a working, reviewable state — not a half-finished pile of changes.

## Steps

1. **Take one task from the plan.** Not the next three "while you're in there" — one.
2. **Apply `minimal-implementation`** while writing it: does this need a new dependency, a new abstraction, a new config option, or does the codebase/stdlib/platform already cover it.
3. **Write the code for that task.**
4. **Verify that task's "done" criteria** from the plan before moving on — run it, check it, don't assume.
5. **Move to the next task.** If something in the plan turns out to be wrong once you're implementing it, stop and flag it rather than silently improvising a different approach — the plan may need a quick update.

## Auto mode

For a fully-specified plan where every task is independently testable, `/build
auto` means: implement every task in sequence without pausing between them for
approval, but still verify each task's done-criteria before moving to the next,
and still stop immediately if a task fails verification or requires a decision
not covered by the plan. Autonomy applies to *pacing*, not to skipping
verification or silently deciding on unresolved questions.

## Handoff

Once all tasks are implemented, move to `/test` to prove the whole thing works,
not just that each task's own narrow check passed.
