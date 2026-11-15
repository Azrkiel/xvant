# Field notes

Where the rules in `SKILL.md` come from. Two projects at the same 36-hour event (November 2026), read from their public git histories. Both used AI coding agents for most of the typing.

- **Project A** won nearly every prize it entered. A hardware-plus-agent demo.
- **Project B** is Albert, our own: a handwriting tutor that writes hints on a PDF. The stronger engineering, and not demoable for most of the weekend.

Git timestamps are self-reported. Neither team's judging was observed.

## Side by side

| | Project A | Project B (Albert) |
|---|---|---|
| Commits | 134 | 262, 104 of them merges |
| First watchable demo | 17 min after the app was scaffolded, scripted on mock data | about 16 h in, a mocked hint on the page |
| Real model driving the screen | about 3 h after the first code commit | about 25 h in; the by-hand live gate never passed |
| Plan | a demo story, then replace the fakes | eight phases and 62 subphases; 28 ticked |
| Tests | some, beside the code | 11,486 lines against 9,495 lines of app code |
| Process commits | few | 48 of 158 non-merge commits touched only docs |
| Submission images in the repo | 13, made on the last night | 0 |
| Submission text first drafted | about 14 h after the first code commit, for one sponsor track | about 31 h in |
| User conversations | 6 listed, 4 before the event | 0; four outreach emails drafted, none sent |
| Prizes entered | 5 sponsor tracks and 3 smaller prizes | 2 sponsor tracks and 1 smaller prize |

## What Project A did

| Habit | Evidence | Rule it became |
|---|---|---|
| Demo first, on fake data | "mock generators and demo story engine", then a "2-minute demo story", within 40 minutes of the first code commit | 5% gate |
| Fakes replaced behind a stable screen | real agent wired in with "demo mode unchanged"; scripted demo deleted only on the last night | thin slice, upgrade queue |
| Simulated mode as the default | README lists it as the default mode | fallback |
| One integrator | one person made 112 of 134 commits | lanes |
| Key logic in one small file | the decision rule is under 50 lines | (worth copying; show it to judges) |
| A physical object and a result on a phone | printed device; pre-alert arrives by text | the moment, the landing |
| One build, many prizes | sponsor integrations of 176 and 380 lines | smallest real use |
| Write-up per track in rubric words | section headings match each sponsor's criteria | submit mode |
| Last night spent on evidence | diagrams and screenshots between 02:00 and 05:00 | 80% gate |

## What slowed Project B

| What happened | Evidence | Rule it became |
|---|---|---|
| Built in layers | capture at hour 3, hint route at hour 12, ink at hour 24 | the Iron Law |
| Production discipline | tests with every subphase, a status file edited in 125 commits, 74 merged pull requests | kit overrides |
| Parallel lanes on shared files | 35 commits about integrating, reconciling or rebasing | disjoint lanes, 15% red flag |
| Built for production inputs | rotated and cropped pages, offline sync, idempotent restore | one happy input |
| Rationed live runs | an 800-call cap and stop-on-failure; the 6-case eval never re-run after its fix | standing approval |
| The human became the queue | twenty-plus by-hand checks waiting | tell the human what to try |
| Scope set late | the product that shipped was scoped at hour 26 | script before plan |
| Off-screen polish | a 180-file brand kit merged four hours before the last commit | red flag |

## What Project B got right, and the skill keeps

- A recorded, keyless mode that replays real input and real model replies.
- A status file that leaves unpassed gates unticked and says what was not claimed.
- A core idea that fits in one sentence.

## Where the line is

Project A's write-up describes a demo "after detecting" its target. Its own validation tables have every measured column empty. The ordering of work is worth copying; that wording is not. This is why the honesty line in `SKILL.md` is the one rule the skill never relaxes.
