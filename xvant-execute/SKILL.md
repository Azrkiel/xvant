---
name: xvant-execute
description: "Use when implementing a written plan with checkpoints, independent parallel tasks or live pairing."
---

Announce “Using xvant-execute to implement this plan.” Read and critique the plan; raise concerns before starting. Draw happy and failure paths with `~/.claude/skills/_shared/ascii-diagram.md` for a human sanity check. Get explicit consent before working on main/master or use xvant-worktree.

Track one todo per task: mark in progress, follow the steps, run the specified checks, then mark complete. Stop and ask at blockers. Route persistent or unexplained failures to xvant-debug. Hand passing work to xvant-ship.

- Subagent-driven: fresh agent per independent task. Review spec compliance then code quality, iterating fixes. Continue between tasks unless blocked or ambiguous. `~/.claude/refs/superpowers/subagent-driven-development/SKILL.md`
- Parallel dispatch: for independent scopes without shared mutable state, use `~/.claude/skills/_shared/parallel-dispatch.md` for briefs/results, then run the full suite on the integrated revision. `~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`
- Live pairing: `~/.claude/refs/gstack/pair-agent/SKILL.md`
