# EconomyLab — validation and benchmark plan

This is a proposed validation plan. No runtime results or benchmark numbers are claimed.

## Domain scenario matrix

| Scenario | Expected behavior | Evidence |
| --- | --- | --- |
| Unaffordable purchase | No partial state mutation | Before/after exact ledger |
| Cooldown tie | Recorded ordering determines eligibility | Hand-solved timestamp trace |
| Infinite free loop | Diagnostic and bounded stop | Minimal config counterexample |
| Unreachable goal | Included as unreached | Completion fraction and boundary |
| Duplicate imported event | Counted once within declared identity | Import audit |
| Parallel cohort run | Same per-run seed yields equivalent result | Run digest comparison |
| Unsupported export mechanic | Reject or explicitly exclude compatible scope | Capability validation report |

## Measurement protocol

Measure simulation events per second, peak memory, cost per agent-hour, and report time across cohort sizes. Record event density and graph complexity. Statistical comparisons use independent runs as their sampling unit where appropriate, disclose seed pairing, and avoid treating thousands of correlated events as independent player evidence.

## Reproducibility record

Record source revision, environment and dependency lock, operating system, CPU/GPU where relevant, workload identity, input size, data distribution, random seeds, concurrency, warm-up policy, repetitions, and output digests. Report variability and failures as well as the preferred statistic. Distinguish pure kernel timing from parsing, serialization, storage, network, and UI costs. Comparisons use the same semantics and workload.

## Correctness before speed

Hand-solved deterministic economies must match event times and balances. Currency sources minus sinks must reconcile to balance change. Reports include the fraction of agents reaching milestones and uncertainty across independent runs. Model assumptions are assessed against playtests before behavioral claims.

Use a small independent reference or analytically solved fixture where feasible. A second implementation that copies the same assumptions is not independent evidence of realism. Numerical comparisons define tolerances; discrete identifiers, units, and state transitions require exact agreement. Every discovered defect becomes a minimized regression scenario with its original cause explained.

## Publication rules

Illustrative values must be labeled. A benchmark badge is added only when its method and source artifacts are available. Missing data, incomplete runs, rejected inputs, and failed experiments remain in the evaluation record. No annualized financial performance, behavioral realism, or platform fidelity is inferred from a short convenient sample.
