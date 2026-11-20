---
name: xvant-hackathon
description: "Use when planning or submitting a timeboxed judged demo, hack weekend, Devpost, sponsor or prize track. Untimed spikes use xvant-prototype."
---

Announce “Using xvant-hackathon to plan this build.” Ask once for hours, team/integrator, demo format/time/device, prize rubrics verbatim, hardware and existing work. A human runs the thin demo path by hand on the demo device before widening scope.

Use `plan-template.md` to maintain one page, `HACKATHON.md`. Write the two-minute spoken script and visible moment/landing first. Cut off-script work with a return condition. Start with one happy input, fake noncore stages, replace them in judge-visible order, and default to a labeled fallback. Map each rubric to real sponsor use and evidence. Allow up to three disjoint lanes with one integrator; the third owns assets.

Convert gate percentages to clock times: 5% watch scripted fake demo; 20% run real input to output by hand; 50% replace script fakes and draft every track; 65% prove the landing; 80% freeze and produce clip, three screenshots and diagram; 90% complete three timed rehearsals and test fallback; 95% confirm submission. Rerun by hand every 3–4 hours. Stop all lanes on breakage.

Before dispatch, copy the rules block in `agent-rules.md` into project AGENTS.md/CLAUDE.md. Use `~/.claude/skills/_shared/parallel-dispatch.md`. Until submission, use the demo plan in place of standard planning, TDD and verification. Commit to main; a human demo run proves completion. Record one replay after freeze.

**Prep:** interview 1–2 real users (name, role, quote and change), read rubrics, order parts, speak the demo. **Submit:** start at 50%, use each track's rubric headings, open with the 20-second moment and a named person's problem. Label all simulation on screen and in writing, give sample sizes for metrics and include three “not checked” lines in README and submission.

Re-plan when lanes stall on approval/budget, work drifts into invisible polish, edge inputs, tests or status logs, or merges/rebases exceed ~15% of commits. Combine lanes for merge churn. Start assets immediately if late. Switch to labeled fallback if hardware is silent at 60%. After submission use xvant-retro, add a row to `field-notes.md`, and rebuild retained projects via brainstorm → plan → TDD.
