---
name: ship
description: Final checklist before merging/deploying a change. Use after /test and /review, right before the change goes out.
---

# /ship

Faster is safer — a small, well-checked change shipped now beats a large
uncertain one sitting in review. The goal here is the final safety pass, not
a rubber stamp.

## Checklist

1. **Tests pass** (from `/test`) and the diff has been reviewed (`/code-review` or equivalent).
2. **No secrets or credentials** in the diff — check anything that looks like a key, token, password, or connection string before committing.
3. **Scope matches the spec.** No unrelated changes riding along in the same commit/PR.
4. **Rollback is possible.** If this breaks something in production, is there a clear way back (revert commit, feature flag, migration is reversible)?
5. **Breaking changes are flagged**, not silently shipped — anything that changes a public API, a database schema, or a contract other systems rely on.
6. **Commit/PR message explains why**, not just what — the diff already shows what changed.

## Output

A short go/no-go with any remaining concerns named explicitly. If something on
the checklist doesn't hold, say so rather than shipping anyway and hoping.

## Note

This skill doesn't perform the actual push/deploy/merge — those are real,
often-irreversible actions and should go through the user's normal
confirmation flow (see the "Executing actions with care" guidance already in
place for git pushes, force operations, etc.). This skill is the checklist that
runs *before* that action, not a replacement for asking first.
