# EconomyLab — milestone roadmap

Milestones are ordered by dependencies, not promised calendar dates. No implementation milestone is complete in this blueprint revision.

| Milestone | Deliverable | Exit criteria |
| --- | --- | --- |
| M0 — Semantics | Economy units and action ordering | Hand-solved cooldown and purchase fixtures |
| M1 — Simulator | Single-agent resource and unlock loop | Conservation and atomicity cases pass |
| M2 — Cohorts | Three policies, session schedules, seeds | Reproduction and independent-stream checks |
| M3 — Reports | Distributions, censoring, comparisons | Unreached agents retained and explained |
| M4 — Game mapping | Narrow Roblox and Shiftcraft contract proposals | Supported mechanics round trip; unsupported ones reject |
| M5 — Calibration | One permissioned playtest dataset | Coverage and model disagreement reported honestly |

## Definition of done

A milestone has a bounded scope, implementation revision, synthetic reproduction input, expected output, validation evidence, and a short demonstration. Setup instructions work in a clean supported environment. Failure behavior is documented alongside the ordinary case. The project status file advances only when the exit criteria are met.

## Scope control

The first milestone cannot depend on a sibling project or hosted service. Optional integrations follow standalone correctness. Performance optimization follows a representative workload and a repeatable baseline. New UI surfaces require a demonstrated user task. Dependencies and licenses are recorded when adopted; exact versions are pinned with implementation.

## Work sequencing

Review [IMPLEMENTATION_HANDOFF.md](IMPLEMENTATION_HANDOFF.md) before creating worktrees. Keep contract changes separate from adapter changes where that allows a reviewer to understand compatibility. A change that invalidates an earlier milestone must update its acceptance evidence and status, not simply append a new roadmap item.

## Deferred expansion

No predicted player retention without empirical validation, real-money purchase optimization, randomized paid reward mechanics, universal Roblox telemetry export, complete behavioral simulation, or factory movement/queue scheduling. Ethical, platform, and audience implications of monetization are separate product decisions.

Open decisions in [DECISIONS.md](DECISIONS.md) should be resolved by a small experiment or a documented requirement. They are not a reason to build every alternative.
