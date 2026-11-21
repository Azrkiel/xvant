---
name: xvant-review-exchange
description: "Use when requesting a separate reviewer, getting pre-merge review, or responding to received review comments."
---

**Send** after each subagent task, major feature and before merge. Assign the reviewer a read-only task ID per `~/.claude/skills/_shared/parallel-dispatch.md`. Give it the change summary, requirements, BASE_SHA and HEAD_SHA. Request strengths, issues by severity and an assessment. Fix Critical now, Important before proceeding, note Minor; explain justified disagreements. `~/.claude/refs/superpowers/requesting-code-review/SKILL.md`

**Receive:** restate the requirement or show the fix. Avoid performative agreement or gratitude. Clarify any ambiguous item before implementing. Check suggestions against usage, target platforms, breakage and actual need. Discuss conflicts with the user's decisions. Fix blocking, then simple, then complex items; test each individually. `~/.claude/refs/superpowers/receiving-code-review/SKILL.md`
