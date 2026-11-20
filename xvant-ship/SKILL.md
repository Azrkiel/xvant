---
name: xvant-ship
description: "Use when verified work is ready to finish, merge, open a PR, keep or discard a branch, or deploy."
---

Announce “Using xvant-ship to complete this work.” Verify tests first and stop on failure. Detect base, worktree and detached HEAD. Offer local merge, push + PR, keep, or discard; omit local merge for detached HEAD. Execute the user's choice. Verify the merge result. Clean up only worktrees you created, for merge/discard only, then delete the branch. Discard needs typed `discard`; force-push needs explicit request. `~/.claude/refs/superpowers/finishing-a-development-branch/SKILL.md`

For a requested release after merge: squash WIP/changelog/version `~/.claude/refs/gstack/ship/SKILL.md`; deploy and canary `~/.claude/refs/gstack/land-and-deploy/SKILL.md`; one-time deploy setup `~/.claude/refs/gstack/setup-deploy/SKILL.md`. Hand off to xvant-release-guard.
