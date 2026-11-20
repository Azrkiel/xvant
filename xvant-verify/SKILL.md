---
name: xvant-verify
description: "Use when asked “is it done?”, “wrap this up”, or about to claim work is fixed, passing or ready to commit. Shipping uses xvant-ship."
---

Before claiming success, run the proving command now. Read the complete output and exit code. On “done” run these in order:

1. Built-in `/verify`: exercise the actual app or feature.
2. xvant-review: review the diff and fix Critical/Important issues. Swarm needs explicit selection at a pre-merge gate.
3. xvant-security: assess the changed surface.
4. xvant-simplify: clean up changed code and verify behavior still passes.

Report evidence for each pass. Claim completion only after all four, then offer xvant-ship. Detailed verification procedure: `~/.claude/refs/superpowers/verification-before-completion/SKILL.md`.
