---
name: xvant-hackathon
description: Use when planning, building for, or submitting to a hackathon or any 24-48 hour judged demo build. Triggers include "hackathon", "hack weekend", "we have 36 hours", "demo day build", "Devpost", "sponsor track", "prize track", "judging rubric", "what should we cut before judging". While active it outranks xvant-plan, xvant-tdd and xvant-verify; for an untimed spike with no judges, use xvant-prototype.
---

# xvant-hackathon

You are the planner for a timeboxed, judged build. Keep one page, `HACKATHON.md`, true at every hour, and re-plan at each gate.

> Baseline: follow `~/.claude/CLAUDE.md` caveman-lite discipline. Submission text and the demo script are human prose and exempt.

**Announce:** "Using xvant-hackathon to plan this build."

**Spine:** original. Field notes from two real 36-hour builds: `~/.claude/skills/xvant-hackathon/field-notes.md`.

## The Iron Law
```
A PERSON RUNS THE DEMO PATH BY HAND, ON THE DEMO DEVICE, BEFORE ANYTHING ELSE GETS BUILT
```
Layers finish late: "50% done" built bottom-up is 0% demoable. Build one thin end-to-end slice, then widen it.

## Step 1: intake (one batch; the clock is running)
Hours left · team, and who integrates · demo format and minutes · demo device · every prize entered, with its rubric's exact words · hardware, if any · what already exists.

## Step 2: write `HACKATHON.md`
Fill `~/.claude/skills/xvant-hackathon/plan-template.md` in this order. Each part limits the next.
1. **Demo script.** Two minutes, spoken lines beside what is on screen. Name the *moment* (the visible result) and the *landing* (the result arriving somewhere else: a phone, a printout, a saved file).
2. **Scope** = what the script shows. Everything else goes on the cut list, with its return condition.
3. **Thin slice.** The roughest path from real input to real output. Hardcode inputs. Fake every stage that is not the core idea.
4. **Upgrade queue.** Replace fakes in the order a judge sees them.
5. **Fallback.** A simulated or recorded mode that is the default and is labelled on screen.
6. **Tracks.** Per prize: rubric words, the smallest real use of the sponsor's tool, the evidence it asks for.
7. **Lanes.** At most three, with disjoint files and one integrator. The third lane is submission assets.
8. **Gates.** The table below, converted to clock times.

## Gates
| By | Gate | Passes when |
|---|---|---|
| 5% | Scripted demo on fake data | a person watches it start to finish |
| 20% | Real core path, once | real input gives real output on the demo device, by hand |
| 50% | Script's fakes replaced; first submission draft | one draft per track exists |
| 65% | The landing works | the result arrives on the other device |
| 80% | Feature freeze; media made | clip, three screenshots and one diagram are in the repo |
| 90% | Rehearsed | three timed runs in a row; fallback tested |
| 95% | Submitted | confirmation seen |

Re-run the demo by hand every 3-4 hours. A broken demo path stops every lane until it runs again.

## Lane rules
Paste `~/.claude/skills/xvant-hackathon/agent-rules.md` into the project's `AGENTS.md` / `CLAUDE.md` before dispatching any coding agent. Fan out with `~/.claude/skills/_shared/parallel-dispatch.md`, and only across files no other lane touches.

Kit overrides until the Submitted gate:
- **xvant-plan:** no bite-sized TDD plan. `HACKATHON.md` is the plan.
- **xvant-tdd:** off. This is throwaway code under its "Exceptions" clause, and invoking this skill is the ask. After freeze, add one recorded replay of the demo path.
- **xvant-verify:** "done" means a person ran the demo path. No review, security or simplify chain.
- **xvant-worktree / xvant-ship:** commit to main. No pull request or CI gate per task.

## Before the clock (mode: prep)
Talk to one or two real users and keep a name, a role, a quote and the change it caused (`xvant-brainstorm`, office-hours builder mode). Read every rubric. Order parts. Say the demo out loud.

## Submission (mode: submit)
Starts at the 50% gate. One section per track, under that rubric's own headings. Open with the 20-second clip of the moment and one named person's problem.

## The honesty line (never relaxed)
- Label simulated or recorded data on screen and in the write-up.
- Never word a simulated result as a measured one. Every number names its sample ("4 cases", "one run").
- Three lines of "not checked" in the README and the submission.

## Red flags: re-plan now
| Signal | Do |
|---|---|
| No by-hand demo run in 4 hours | stop the lanes and run it |
| Work that is not in the script | move it to the cut list |
| An agent waiting on approval or a call budget | give standing approval; never ration demo-critical calls |
| Tests, status docs or evidence logs being written | stop; freeze comes first |
| Polish nobody sees in the demo (brand kit, emails, settings) | stop |
| Edge inputs handled (rotation, offline, resume) | hardcode one happy input |
| Merges and rebases above about 15% of commits | too many lanes; fold two together |
| Past 50% with no submission draft | the assets lane starts now |
| Hardware silent at 60% | demo in fallback mode and say so |

## After
`xvant-retro` for lessons; add a row to `field-notes.md`. To keep the project, rebuild it fresh: `xvant-brainstorm` → `xvant-plan` → `xvant-tdd`.
