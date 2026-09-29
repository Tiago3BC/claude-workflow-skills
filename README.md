# claude-workflow-skills

Nine custom Claude Code skills covering a spec → plan → build → test → ship
engineering workflow, plus a "minimal implementation" principle that pushes
toward simpler solutions (fewer unnecessary abstractions, native/stdlib
features first, YAGNI).

Written from scratch, no external dependencies or executable code — each skill
is a single readable markdown file.

## Skills

| Skill | Purpose |
|---|---|
| `minimal-implementation` | Simplicity ladder: YAGNI → reuse → stdlib → native → existing dependency → one-liner → minimum new code |
| `spec` | Turn an idea into a written spec before coding |
| `plan` | Break an agreed spec into small ordered tasks |
| `build` | Implement plan tasks one at a time (supports `/build auto`) |
| `test` | Prove the implementation works, including edge cases |
| `tdd` | Strict red-green-refactor workflow |
| `constraints` | Decide the quality bar once, up front, and enforce it |
| `webperf` | Measure-first web performance auditing |
| `ship` | Final pre-merge/deploy checklist |

## Install

Copy the skill folders you want into your Claude Code skills directory:

```bash
git clone https://github.com/Tiago3BC/claude-workflow-skills.git
cp -r claude-workflow-skills/skills/* ~/.claude/skills/
```

Or copy just one skill:

```bash
cp -r claude-workflow-skills/skills/spec ~/.claude/skills/spec
```

Optionally, add the "Code simplicity" ladder to your `~/.claude/CLAUDE.md` so
it's always active rather than only available on explicit `/minimal-implementation`
invocation — see the checklist inside `skills/minimal-implementation/SKILL.md`.

## Suggested workflow

```
idea/problem
  → /spec
  → /plan
  → /build            (applies minimal-implementation while writing code)
  → /test or /tdd
  → /code-review       (built into Claude Code)
  → /webperf           (where relevant)
  → /ship
```
