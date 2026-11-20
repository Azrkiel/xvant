---
name: xvant-write-skill
description: "Use when creating, editing, scaffolding or testing a skill or SKILL.md, including skillify exports."
---

For new skills and edits, run a pressure scenario with a subagent without the skill. Capture the failure and verbatim rationalizations. Write the smallest instruction that addresses them; rerun with the skill, verify compliance and close loopholes.

Frontmatter: name (letters, numbers, hyphens) and description under 1024 characters total. Describe when to use it in third person, starting “Use when”. Include distinct trigger words; mark explicit-only skills accordingly. Keep workflow in the body. Use one strong example, references for detail, diagrams only for non-obvious decisions, and red flags/rationalizations for discipline skills.

Template/scaffolding: `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/skill-creator/skills/skill-creator/SKILL.md`. Authoring guidance: `~/.claude/refs/anthropic-skills/productivity/write-a-skill/SKILL.md`, `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/plugin-dev/skills/skill-development/SKILL.md`. Skillify export: `~/.claude/refs/gstack/skillify/SKILL.md`. Pressure testing: `~/.claude/refs/superpowers/writing-skills/SKILL.md`. Prefer tested behavior when conventions differ.
