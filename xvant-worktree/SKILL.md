---
name: xvant-worktree
description: Use when starting feature work that needs isolation from the current workspace, or before executing an implementation plan — ensures an isolated workspace exists via native tools or a git worktree fallback. Triggers include "isolate this", "set up a worktree", "work on a branch", before risky multi-file changes.
---

# xvant-worktree

Ensure work happens in an isolated workspace. Detect first, prefer native tools, fall back to git. Never fight the harness.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

**Announce:** "Using xvant-worktree to set up an isolated workspace."

## Steps (spine: superpowers using-git-worktrees)
0. **Detect existing isolation.** Compare git-dir vs git-common-dir; guard against submodules (`git rev-parse --show-superproject-working-tree`). If already in a linked worktree, skip creation. If in a normal checkout, ask consent before creating one (unless the user already declared a preference).
1. **Create:** prefer a native worktree tool (e.g. `EnterWorktree`, a `/worktree` command, `--worktree` flag) — it handles placement, branch, cleanup. Only if none exists, use `git worktree add`. For project-local dirs (`.worktrees/` preferred), verify it's gitignored first (`git check-ignore`); add + commit to `.gitignore` if not. Sandbox/permission error → work in place and say so.
2. **Setup:** auto-detect and run install (npm/cargo/pip/poetry/go) as applicable.
3. **Baseline:** run tests. Pass → report ready. Fail → report and ask before proceeding.

Report: worktree path, branch, baseline test result. Full reference: `~/.claude/refs/superpowers/using-git-worktrees/SKILL.md`. Pairs with `xvant-execute` and `xvant-ship`.
