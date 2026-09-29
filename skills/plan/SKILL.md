---
name: plan
description: Turn an agreed spec into a small ordered list of atomic, verifiable implementation tasks. Use after /spec, before writing code, whenever a task touches more than one file or has more than one reasonable implementation approach.
---

# /plan

Small, atomic tasks. The goal is a task list where each item is independently
completable, testable, and small enough to review in one pass.

## Steps

1. **Break the spec's scope into tasks.** Each task should be a single coherent change: one component, one endpoint, one migration — not "implement the feature" as one task.
2. **Order tasks by dependency**, not by perceived importance. What has to exist before the next task can start.
3. **For each task, note:**
   - What file(s) it touches
   - What "done" looks like for that specific task (testable, not vague)
   - Whether it needs a new dependency, and if so, check `minimal-implementation` first — is there already a way to do this without adding one
4. **Flag architectural decisions explicitly** rather than deciding silently mid-plan if there's a real fork in approach (e.g. "state management: Context vs a library" — this is a call worth surfacing, not silently picking one).
5. **Keep tasks small enough** that if one goes wrong, the blast radius is one task, not the whole feature.

## Output

A numbered task list, each with: what changes, what file(s), what "done" means.
For genuinely complex work, this is a good point to use Claude Code's own
EnterPlanMode instead of just narrating a list, so the user explicitly approves
the plan before implementation starts.

## Handoff

Once the plan is approved, move to `/build` and work through tasks one at a
time — don't jump ahead or batch multiple tasks into one uncommitted blob.
