# EconomyLab — implementation handoff

## Read order

Read PRODUCT, DATA_MODEL, PIPELINE, and VALIDATION before selecting a work package. This repository currently contains documentation and original identity artwork only. Do not infer an executable stack from proposed folder names.

## Proposed module hierarchy

| Planned path | Responsibility | Dependency boundary |
| --- | --- | --- |
| sim/ | Scheduler, resource reducer, agent interfaces | Independent of rendering and platform |
| analysis/ | Censoring, cohort metrics, sensitivity | Reads accepted simulation outputs |
| workbench/ | Economy editor and reports | No direct canonical state mutation |
| adapters/ | Roblox, Shiftcraft, and experiment mappings | Explicit supported mechanics |
| contracts/ | Economy and simulation schemas | Versioned domain ownership |
| fixtures/ | Analytically solved economies | Small public examples |

## First work packages

| Package | Deliverable | Acceptance / review |
| --- | --- | --- |
| WP-01 | Economy schema and affordability rules | Graph validation and units review |
| WP-02 | Discrete scheduler and ledger | Hand-solved upgrade fixture |
| WP-03 | Cohort policies and random streams | Same-run reproduction and session boundaries |
| WP-04 | Completion and censoring report | Unreached-goal counterexample |
| WP-05 | One game adapter | Config round trip and unsupported-feature rejection |

## Engineering discipline

Each work package should fit one reviewable behavior. Define the fixture and expected output before broadening the interface. Keep domain code independent of the UI and external adapters. Add meaningful tests for state transitions, failure recovery, and numerical semantics; avoid tests that simply restate an implementation. When a contract changes, update its fixture and every affected importer together or preserve a compatibility layer.

Use a short-lived feature branch from main. A worktree is optional and should correspond to a bounded task; no permanent development branch is required. Commit the smallest coherent change with its documentation and validation evidence. Merge only after the package's acceptance criteria are met. Do not add empty frameworks, unverified installation commands, dummy benchmark results, or success badges.

## First reviewer checklist

The reviewer can explain where canonical state lives, what event order means, which values carry units, how a retry is recognized, and how a partial result is rejected. The reviewer can reproduce the smallest scenario without credentials or another project. A larger implementation plan should be revised from the observed first slice rather than treating every proposed directory as a requirement.
