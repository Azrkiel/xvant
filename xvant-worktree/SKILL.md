---
name: xvant-worktree
description: "Use when starting isolated feature work, setting up a worktree or preparing a workspace for plan execution."
---

Announce “Using xvant-worktree to set up an isolated workspace.” Compare git-dir with git-common-dir and check `git rev-parse --show-superproject-working-tree` for submodules. Reuse linked worktrees. In a normal checkout ask before creating one unless a preference already exists.

Prefer EnterWorktree, /worktree or --worktree. Otherwise use `git worktree add`. For a project-local directory (prefer .worktrees/), verify with `git check-ignore`; add and commit its ignore rule if needed. On sandbox/permission failure, work in place and disclose it.

Detect and install project dependencies, then run baseline tests. Report path, branch and result. Ask before proceeding on failure. `~/.claude/refs/superpowers/using-git-worktrees/SKILL.md`
