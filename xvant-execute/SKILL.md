---
name: xvant-execute
description: Use when you have a written implementation plan and need to execute its tasks in this session with review checkpoints. Triggers include "execute the plan", "run the plan", "work through the tasks", "start implementing the plan". For parallelizable independent tasks, see the subagent and parallel modes below.
---

# xvant-execute ◆

Load a plan, review it critically, execute its tasks, verify, report.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.
> Entry step: before writing the first unit of code, follow `~/.claude/skills/_shared/ascii-diagram.md` and draw the flow (happy + unhappy paths). Let the human sanity-check it.

**Announce:** "Using xvant-execute to implement this plan."

## Spine (superpowers executing-plans)
1. Read the plan. Review critically — raise concerns BEFORE starting. Create a todo per task.
2. Per task: mark in_progress → follow each step exactly → run the specified verifications → mark complete. Don't skip verifications.
3. Never start implementation on main/master without explicit consent (use `xvant-worktree`).
4. **Stop and ask** on any blocker (missing dep, failing test, unclear instruction, repeated verification failure). Don't guess. On a persistent or root-cause-unclear test failure, hand to `xvant-debug` before attempting a fix.
5. After all tasks pass, hand to `xvant-ship` to finish the branch.

## Mode: subagent-driven (graft)
When tasks are mostly independent and you want continuous in-session execution: dispatch a fresh subagent per task, then two-stage review each — spec compliance first, then code quality — looping fixes until both pass. Don't pause to check in between tasks; only stop on BLOCKED/ambiguity/done. Full: `~/.claude/refs/superpowers/subagent-driven-development/SKILL.md`.

## Mode: parallel dispatch (graft)
For 2+ truly independent problems (different files/subsystems, no shared state): one focused agent per domain, each with specific scope + constraints + expected output, run concurrently, then verify no conflicts and run the full suite. Full: `~/.claude/refs/superpowers/dispatching-parallel-agents/SKILL.md`.

## Mode: pair-agent (graft, gstack)
For live pairing/tunneled collaboration: `~/.claude/refs/gstack/pair-agent/SKILL.md`.
