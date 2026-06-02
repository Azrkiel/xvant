---
name: xvant-security
description: Use ONLY when explicitly asked for a security pass — "security check", "security review", "security audit", "is this safe", "check for vulnerabilities". Does NOT self-trigger on a bare "done" (xvant-verify orchestrates that and calls this).
---

# xvant-security

Security audit of the pending change. Explicit-invoke only.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Security warnings: write in full, not terse.

**Spine:** the built-in `/security-review` command — review pending changes on the current branch for vulnerabilities (injection, authz/authn, secrets, unsafe deserialization, SSRF, path traversal, etc.).

## Mode: deep audit (graft, gstack cso)
For a structured OWASP Top 10 + STRIDE threat-model pass on a feature or surface, follow the Chief Security Officer procedure: `~/.claude/refs/gstack/cso/SKILL.md`.

## Reporting
Rank findings by severity with concrete exploit path and fix. Never claim "secure" without stating what you checked. Sequenced as step 3 of `xvant-verify`.
