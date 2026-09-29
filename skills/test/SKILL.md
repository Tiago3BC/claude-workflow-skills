---
name: test
description: Prove an implementation actually works, beyond just "it compiled." Use after /build, before /review, whenever code changes behavior.
---

# /test

Tests are proof, not paperwork. The goal is evidence the change does what it
claims, including at the edges, not just a green checkmark on the happy path.

## Steps

1. **Run the existing test suite first.** A change that breaks something unrelated needs to be caught before adding new tests on top.
2. **Cover the acceptance criteria from the spec**, not just whatever's easiest to test. If the spec said "handles empty input," there should be a test for empty input.
3. **Test the edges, not just the middle:** empty/null input, the boundary values (0, max, off-by-one), concurrent/repeated calls if relevant, failure paths (network error, invalid data) not just success paths.
4. **For UI changes**, actually run the app and use the feature — a passing test suite doesn't prove the feature works for a real user. Say explicitly if this wasn't possible (no way to run the UI here) rather than claiming it was verified.
5. **Don't write a test that can't fail.** A test that passes regardless of whether the code is correct is worse than no test — it's false confidence.

## Output

A short summary: what was tested, what passed, and anything that couldn't be
verified (and why), rather than a bare "tests pass."

## Handoff

Once tests pass and edges are covered, move to `/review` (the existing
`/code-review` skill in this environment handles that) before `/ship`.
