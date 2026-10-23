# EconomyLab — pipeline specification

## Stage contracts

| Stage | Input | Output / postcondition | Failure and recovery |
| --- | --- | --- | --- |
| Validate configuration | Currencies, actions, costs, rewards, unlock graph | Accepted EconomyConfig | Reject cycles where unsupported, negative quantities, and missing references |
| Instantiate cohort | Agent policies, session schedules, seeds | Independent simulation initial states | Record behavior assumptions and seed derivation |
| Schedule actions | Current state + eligible agent action | Ordered action and cooldown events | Invalid action cannot spend unavailable resources |
| Apply transitions | Action effects + resource ledger | Balances, inventory, unlocks, and flow events | Atomic action prevents partial spend/reward effects |
| Observe progression | Run events + milestone definitions | Reached/unreached goals and waiting reasons | Do not drop agents that fail to reach a milestone |
| Compare scenarios | Baseline/candidate + paired seed set | Distribution and sensitivity reports | Incompatible behavior or observation windows are flagged |
| Export and calibrate | Accepted config + supported telemetry mapping | Versioned candidate and model-fit notes | Roblox or game adapter validates capabilities before use |

## Ordering and checkpoints

Events use integer simulation time with a recorded unit and deterministic tie policy for rewards, cooldown expiration, purchases, and session endings. A purchase uses the balance at its scheduled action event. Pausing between sessions has explicit cooldown behavior. Checkpoints include resource state, agent state, pending events, and named random-stream states. Config comparisons record whether seed pairing remains meaningful after a structural change.

## Invariants across stages

- Currency and inventory values use exact integer base units unless a specific scale is declared.
- Every resource mutation has an action, source/sink category, and configuration revision.
- Purchases require affordability and prerequisites at the moment of transition.
- Reached and unreached milestones both contribute to cohort reporting.
- Simulated agent policies are assumptions and do not establish real player preferences.

## Completion protocol

An operation starts by assigning a run identity and fingerprinting its effective configuration. Input validation completes before irreversible domain effects. Intermediate files remain staged and include an incomplete marker. Completed outputs are hashed and referenced by a manifest committed atomically with their accepted status. A crash before publication leaves recoverable intermediate work, not a plausible final report.

Retries identify the prior operation and preserve the original input references. A repair that changes semantics becomes a new revision with an explicit reason. Cancellation is honored at documented boundaries and records the last committed checkpoint. Importers reject incomplete outputs by default; diagnostic tools can inspect them only with an explicit incomplete status.

## Worked scenario

Illustrative economy: an action grants 5 coins every 10 simulated seconds; an upgrade costs 20 and doubles the grant. With the first grant at time 10, a simple buy-as-soon-as-affordable policy purchases at time 40 under a specified same-time ordering. Changing the price to 25 moves purchase timing. A session ending at time 35 prevents purchase in that session. These hand-solved cases establish scheduler and affordability semantics.

## Pipeline acceptance gate

The first vertical slice must demonstrate one ordinary case, one malformed input, one duplicate, and one interruption or recovery case. Its output includes input lineage and enough diagnostics to explain failure without reconstructing the operator's shell history. Domain-specific scenarios in [VALIDATION.md](VALIDATION.md) take precedence over generic throughput goals.
