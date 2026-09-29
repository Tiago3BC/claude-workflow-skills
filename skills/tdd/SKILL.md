---
name: tdd
description: Test-driven development — write a failing test before the implementation, then make it pass, then refactor. Use when the user explicitly asks for TDD, or for well-specified logic where the expected behavior can be stated as test cases up front.
---

# /tdd

Red, green, refactor, enforced in that order.

## Steps

1. **Red:** write a test for the next small piece of behavior, based on the spec's acceptance criteria. Run it. Confirm it fails (and fails for the right reason — not a typo/syntax error).
2. **Green:** write the minimum code to make that test pass. Apply `minimal-implementation` here — the point is the smallest change that passes, not the most elegant one yet.
3. **Refactor:** with the test passing as a safety net, clean up the implementation (remove duplication, improve naming) without changing behavior. Re-run the test after refactoring to confirm it still passes.
4. **Repeat** for the next piece of behavior.

## Rules

- Never write implementation code before its test exists and has been confirmed to fail.
- Never skip the refactor step and call it done — green-but-messy isn't the end state.
- Keep each red-green-refactor cycle small (minutes, not hours) — if a test requires a huge implementation to pass, the test is testing too much at once.

## When not to use this

Not every task benefits from strict TDD — exploratory spikes, throwaway
scripts, or UI layout work where the "test" would just re-describe the
implementation aren't good fits. Use `/test` (write tests after implementation)
for those instead.
