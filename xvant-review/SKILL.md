---
name: xvant-review
description: "Use ONLY when explicitly asked “review this”, “code review”, “review PR” or “deep/swarm review”. Separate reviewer feedback uses xvant-review-exchange."
---

For an explicit code review or xvant-verify step 2, use built-in `/code-review` on changed code (low to max effort; `--comment` for inline PR feedback, `--fix` to apply findings). For a GitHub PR use built-in `/review`.

- For developer experience, check API ergonomics, naming, onboarding and errors with `~/.claude/refs/gstack/devex-review/SKILL.md`.
- Only for an explicit swarm/deep review, follow [swarm.md](swarm.md) in order, including its isolation requirements and evidence labels.

Fix Critical issues immediately, Important before proceeding, note Minor; give technical reasons when disputing a finding. Route a separate reviewer's feedback to xvant-review-exchange, a dedicated security pass to xvant-security, and quality-only cleanup to xvant-simplify.
