---
name: xvant-repo-guard
description: Use to protect a git repo from bad commits — set up pre-commit hooks, git guardrails, and secret/PII redaction before pushing. Triggers include "set up pre-commit", "add git guardrails", "stop bad commits", "redact secrets before push", "protect main". Not for general settings (use xvant-configure).
---

# xvant-repo-guard

Guardrails that keep the repo clean: pre-commit checks, commit hygiene, secret/PII redaction.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Secret/leak warnings: write in full.

**Spine:** git-guardrails — Claude-Code-aware git safety (no `git add -A`, no force-push without ask, branch protection): `~/.claude/refs/anthropic-skills/misc/git-guardrails-claude-code/SKILL.md`.

## Graft modes
- **Pre-commit setup** (hooks, linters, formatters on commit): `~/.claude/refs/anthropic-skills/misc/setup-pre-commit/SKILL.md`.
- **Careful mode** (extra confirmation on risky ops): `~/.claude/refs/gstack/careful/SKILL.md`.
- **Guard** (gating checks): `~/.claude/refs/gstack/guard/SKILL.md`.
- **Redaction** (credentials/PII/legal before an external sink) via gstack's `bin/gstack-redact` engine — scan the exact bytes you will send.

For automating these as harness hooks, see `xvant-configure` / `xvant-extend`.
