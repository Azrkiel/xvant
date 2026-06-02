---
name: xvant-write-skill
description: Use when creating a new skill, editing an existing skill, or verifying a skill works before deployment. Triggers include "write a skill", "create a skill", "edit this skill", "make a SKILL.md", "skillify this". Covers authoring, the YAML description rules, and testing skills with pressure scenarios.
---

# xvant-write-skill

Writing skills IS TDD for process documentation.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline.

## Iron Law (spine: superpowers writing-skills)
```
NO SKILL WITHOUT A FAILING TEST FIRST
```
Applies to new skills AND edits. Test = a pressure scenario run with a subagent WITHOUT the skill (watch it fail, capture verbatim rationalizations) → write the minimal skill addressing those → re-run WITH the skill (it complies) → close loopholes.

## Description rules (critical for triggering)
- Frontmatter needs `name` (letters/numbers/hyphens) and `description`, <1024 chars total.
- Description = WHEN to use (triggering conditions, symptoms, keywords), third person, start with "Use when…". **Never summarize the workflow** — that creates a shortcut the agent follows instead of reading the body.
- Where a skill should only fire on explicit request, say so ("Use ONLY when explicitly asked…").
- Distinct trigger keywords so two skills don't fire on the same phrase.

## Quality
Token-efficient (move detail to refs, cross-reference don't copy). One excellent example over many. Small flowchart only for non-obvious decisions. Rationalization table + red-flags for discipline skills. Self-contained file or supporting files for heavy reference/tools.

## Graft modes
- **Scaffolding** a new skill from a template: `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/skill-creator/skills/skill-creator/SKILL.md`.
- **Anthropic best-practice authoring**: `~/.claude/refs/anthropic-skills/productivity/write-a-skill/SKILL.md` and `~/.claude/plugins/marketplaces/claude-plugins-official/plugins/plugin-dev/skills/skill-development/SKILL.md`.
- **gstack export format** (skillify): `~/.claude/refs/gstack/skillify/SKILL.md`.

Full reference: `~/.claude/refs/superpowers/writing-skills/SKILL.md`. Note: superpowers' philosophy and Anthropic's published guidance differ — prefer tested behavior over format compliance.
