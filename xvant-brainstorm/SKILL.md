---
name: xvant-brainstorm
description: "Use when exploring a new idea, feature or behavior before design approval. Includes product office hours."
---

Announce “Using xvant-brainstorm to shape this before we build.” Get design approval before coding or scaffolding, even for small changes.

1. Read relevant files, docs and recent commits. Separate independent subsystems.
2. Ask one question per turn about purpose, constraints and success criteria. Prefer multiple choice.
3. Present 2–3 approaches with trade-offs and a recommendation. Present the design in sections and get approval for each.
4. Save the spec to `docs/specs/YYYY-MM-DD-<topic>.md` (beside the work outside Git). Resolve placeholders, contradictions, scope gaps and ambiguity. Have the user review it, then hand off to xvant-plan.

For product ideas, first run Office Hours (`~/.claude/refs/gstack/office-hours/SKILL.md`), skipping the telemetry/gbrain preamble. Startup mode asks for concrete evidence on demand, status quo, desperate specificity, narrowest wedge, observation and future-fit. Builder mode uses collaborative design thinking for learning, OSS, side projects and hackathons. Deliver a design document.
