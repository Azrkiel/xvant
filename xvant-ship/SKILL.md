---
name: xvant-ship
description: Use when implementation is complete and verified and you need to integrate and release the work — finish the branch (merge/PR/keep/discard), or deploy. Triggers include "ship it", "finish this branch", "merge this", "open a PR", "deploy this", "land and deploy".
---

# xvant-ship

Integrate finished work, then optionally deploy. Verify tests pass first.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Destructive-action confirmations: write in full.

**Announce:** "Using xvant-ship to complete this work."

## Mode: finish the branch (spine: superpowers finishing-a-development-branch)
1. **Verify tests pass** — if failing, stop; cannot merge/PR until green.
2. **Detect environment** (normal repo / worktree named branch / detached HEAD) and base branch.
3. **Present exactly these options** (3 for detached HEAD — no local merge):
   1) Merge to base locally  2) Push + open PR  3) Keep branch as-is  4) Discard
4. **Execute the choice.** Merge first, verify tests on the result, then clean up the worktree (only for Merge/Discard — Push/Keep preserve it), then delete the branch. Discard requires a typed `discard` confirmation. Never force-push without explicit request; only clean up worktrees you created.

Full: `~/.claude/refs/superpowers/finishing-a-development-branch/SKILL.md`.

## Mode: deploy (graft, gstack)
After merge, when the user wants to release:
- Ship workflow (squash WIP, changelog, version): `~/.claude/refs/gstack/ship/SKILL.md`
- Merge → deploy → canary-verify: `~/.claude/refs/gstack/land-and-deploy/SKILL.md`
- One-time deploy config: `~/.claude/refs/gstack/setup-deploy/SKILL.md`

After a deploy, hand to `xvant-release-guard` to watch it.
