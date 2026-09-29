---
name: spec
description: Turn an idea or problem statement into a clear written spec before any code is written. Use at the start of a non-trivial task, when requirements are vague, or when the user asks to "spec out" or "define" something.
---

# /spec

Spec before code. The goal is a short written document that pins down what's
being built and why, so implementation choices later aren't guesswork.

## Steps

1. **State the problem in one or two sentences.** What's broken or missing, for whom.
2. **List what's in scope and what's explicitly out of scope.** Scope creep starts here if you skip this.
3. **Write the acceptance criteria** — concrete, checkable statements of "this is done when...". Not vague goals like "improve performance"; specific ones like "p95 API latency under 200ms for the /search endpoint".
4. **Note constraints** that shape the solution: existing architecture, must-support platforms, deadlines, backward-compatibility requirements.
5. **Flag open questions** rather than silently assuming an answer. If a real decision is needed from the user (not something you can reasonably infer), use AskUserQuestion instead of guessing.
6. **Keep it short.** A spec that takes 10 minutes to read won't get read. Aim for something that fits on one screen for most tasks; only go longer for genuinely large features.

## Output

A short markdown spec (in the conversation, or as a file if the user wants it
persisted) with these sections: Problem, Scope (in/out), Acceptance criteria,
Constraints, Open questions.

## Handoff

Once the spec is agreed, move to `/plan` to break it into implementation tasks.
Don't start writing code directly from a spec — plan first, even briefly.
