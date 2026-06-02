---
name: xvant-docs
description: Use to generate or update documentation — tutorials, how-tos, reference, explanation (Diataxis), release notes, a landing page, or to render docs to PDF, or to edit an article for clarity. Triggers include "write the docs", "document this feature", "generate a reference", "release notes", "make a PDF", "edit this article". Not for CLAUDE.md (use xvant-claude-md).
---

# xvant-docs

Generate and maintain human documentation.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline for chat; the docs themselves are human-facing prose — write those to read well.

**Spine:** gstack document-generate — Diataxis doc generator (tutorial / how-to / reference / explanation): `~/.claude/refs/gstack/document-generate/SKILL.md`.

## Graft modes
- **Post-ship doc updates + coverage map**: `~/.claude/refs/gstack/document-release/SKILL.md`.
- **Render to PDF**: `~/.claude/refs/gstack/make-pdf/SKILL.md`.
- **Landing page / report**: `~/.claude/refs/gstack/landing-report/SKILL.md`.
- **Edit an existing article for clarity/voice**: `~/.claude/refs/anthropic-skills/personal/edit-article/SKILL.md`. When humanizing prose, defer to the `humanizer` skill.
