---
name: xvant-execute
description: "Use when implementing a written plan with checkpoints, independent parallel tasks or live pairing."
---

Announce “Using xvant-execute to implement this plan.” Read and critique the plan; raise concerns before starting. Draw happy and failure paths with `~/.claude/skills/_shared/ascii-diagram.md` for a human sanity check. Get explicit consent before working on main/master or use xvant-worktree.

Track progress in the written plan. For every delegated task use `~/.claude/skills/_shared/parallel-dispatch.md` for the worker’s brief, checkoff and result. When working solo, check off the same row after its acceptance check passes. Stop and ask at blockers. Route persistent or unexplained failures to xvant-debug. Run xvant-verify on the integrated result before xvant-ship.

- Subagent-driven: fresh agent per independent task. Review spec compliance then code quality, iterating fixes. Continue between tasks unless blocked or ambiguous. `~/.claude/refs/superpowers/subagent-driven-development/SKILL.md`
- Parallel dispatch: for independent scopes without shared mutable state, batch the ready task IDs, then run the full suite on the integrated revision. `~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`
- Live pairing: `~/.claude/refs/gstack/pair-agent/SKILL.md`
