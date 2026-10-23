# EconomyLab — product specification

## Intended outcome

Build a versioned discrete-event economy simulator with explicit agent policies, progression graphs, resource ledgers, and comparative reports. Begin with Roblox-style soft-currency economies and keep the core reusable for independent games. Treat synthetic player behavior as a testable assumption rather than a prediction of real players.

## Primary users and jobs

| User | Job | Successful outcome |
| --- | --- | --- |
| Roblox creator | Compare upgrade and reward changes | Identify bottlenecks and resource accumulation before release |
| Game designer | Understand progression pacing | Inspect distributions and reasons for waiting |
| Simulation researcher | Evaluate agent assumptions | Reproduce a run and compare it with observed play |

## First journey

A designer changes the price of the third upgrade and runs the old and new economies across the same seed set and three agent policies. The report shows completion distributions, unreached milestones, idle periods, balances, and resource sources/sinks. The designer opens a slow run to identify the affordability condition that stopped progress, then exports a candidate configuration for an isolated game test.

## Functional requirements

| ID | Requirement | Acceptance evidence |
| --- | --- | --- |
| FR-01 | Validate config graph and units | Missing references and unsupported cycles fail before simulation |
| FR-02 | Keep actions atomic | Failed purchase cannot consume currency or grant partial benefits |
| FR-03 | Record resource flows | Every balance change points to a source or sink event |
| FR-04 | Preserve unreached milestones | Completion fractions accompany time-to-goal statistics |
| FR-05 | Pair scenario randomness carefully | Seed streams and policy/config differences recorded |
| FR-06 | Declare adapter coverage | Unsupported game mechanics reject export or remain explicit |

## Scope and product constraints

One soft currency, a small prerequisite graph, deterministic and probabilistic rewards, cooldowns, session boundaries, three transparent agent policies, paired-seed comparisons, unreachable-goal diagnostics, and a local report. Add a Roblox mapping only after the independent simulator is validated.

No predicted player retention without empirical validation, real-money purchase optimization, randomized paid reward mechanics, universal Roblox telemetry export, complete behavioral simulation, or factory movement/queue scheduling. Ethical, platform, and audience implications of monetization are separate product decisions.

## Product quality requirements

Every visible result identifies its source version and completeness. Repeating an action cannot silently create duplicate domain effects. Invalid input produces an actionable diagnostic tied to the field or event that failed validation. Long operations report progress and cancellation boundaries. A cancelled or interrupted operation is visibly different from a completed one.

The initial deployment is a single-user local workflow. Collaboration, tenancy, mobile apps, hosted services, billing, and distributed orchestration are separate scope decisions. An interface proposal must explain the user task it supports before adding new screens or infrastructure.

## Success and non-success

Hand-solved deterministic economies must match event times and balances. Currency sources minus sinks must reconcile to balance change. Reports include the fraction of agents reaching milestones and uncertainty across independent runs. Model assumptions are assessed against playtests before behavioral claims.

Repository stars, document length, and interface polish do not substitute for the domain acceptance criteria. A result that cannot be explained or reproduced remains provisional. Scope expansion is deferred until the first complete scenario can be demonstrated and reviewed.

## Open product decisions

- Which first game economy provides a realistic but bounded example?
- What observation window and session policies reflect the intended test?
- Which playtest events can be collected with appropriate permissions and privacy boundaries?
