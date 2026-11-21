# HACKATHON.md template

Copy to the project root as `HACKATHON.md`. Keep it to one page. Update it at every gate; delete lines that stop being true.

```markdown
# <Project>: <one line a judge would repeat>

Event: <name> · Hacking: <start> to <deadline> (<N> h) · Demo: <table or stage>, <minutes> min, on <device>
Team: <name: lane> · Integrator: <name>

## Demo script (2 min)
| Time | Say | On screen |
|---|---|---|
| 0:00 | <one named person's problem> | <title or the device> |
| 0:20 | <what they do> | <input happening live> |
| 0:50 | <the moment> | <the visible result> |
| 1:20 | <the landing> | <result arriving on the other device> |
| 1:45 | <what is real, what is simulated, what is next> | <one diagram> |

## Thin slice (due at the 20% gate)
<real input> -> <core step> -> <real output>
Faked for now: <stage: how it is faked>

## Upgrade queue (the order a judge sees)
- [ ] H1 <judge-visible upgrade> | <lane> | <what the human should see>
- [ ] H2 <judge-visible upgrade> | <lane> | <what the human should see>

## Fallback
Mode: <simulated / recorded>, default on, labelled "<label>" on screen.
Switch to live with: <flag or toggle>

## Tracks
| Prize | Rubric words | Smallest real use | Evidence asked for | Draft |
|---|---|---|---|---|
| <track> | <criteria, verbatim> | <one feature> | <photo, quote, link> | [ ] |

## Lanes
| Lane | Owner | Owns these files |
|---|---|---|
| Screen | | |
| Core | | |
| Assets | | submission text, clip, screenshots, diagram |

## Gates
| Gate | Clock time | Passed at |
|---|---|---|
| Scripted demo on fake data (5%) | | |
| Real core path, once (20%) | | |
| Fakes replaced; first drafts (50%) | | |
| Landing works (65%) | | |
| Freeze; media made (80%) | | |
| Rehearsed three times (90%) | | |
| Submitted (95%) | | |

By-hand demo runs: <time, pass or fail>, ...

## Cut list
| Cut | Comes back only if |
|---|---|
| <feature> | <condition, or "after the event"> |

## Not checked
- <what is simulated>
- <what was run once, not repeated>
- <what no person has tried>
```

## Filling it in

- **The one line** is what a judge tells the next judge. If it needs "and", cut scope.
- **The moment** must be visible from two metres away: ink appearing, a map lighting up, a device moving.
- **The landing** is what makes it feel finished: a text arrives, a file opens elsewhere, a second screen updates.
- **Smallest real use** means the sponsor's tool does one real job in the demo path. A feature bolted on outside the script earns nothing.
- **Clock times** come from the gate percentages times the event length. For 36 hours: 2 h, 7 h, 18 h, 23 h, 29 h, 32 h, 34 h.
- **Not checked** goes into the README and the submission as written.
