# EconomyLab — data model

## Canonical entities

| Entity | Identity / fields | Lifecycle / invariant |
| --- | --- | --- |
| EconomyConfig | Currencies, actions, costs, rewards, prerequisites, version | Immutable during accepted comparison run |
| AgentPolicy | Observation access, choice rule, session schedule, version | Transparent behavior assumptions |
| SimulationRun | Config, policy, seed streams, observation window | Terminal status and event budget preserved |
| ResourceEvent | Run, time, action, asset, signed amount, source/sink | Every mutation accounted for |
| MilestoneObservation | Goal, reached flag, time or censoring boundary | Unreached is not missing or zero |
| ComparisonReport | Run groups, seed pairing, metrics, uncertainty | Behavior and window compatibility stated |

## Domain semantics

Time-to-goal distributions require a censoring policy. A mean calculated only among agents who reach a goal can improve while more agents fail; show both completion rate and conditional timing. Balance distributions identify hoarding, insufficient sinks, and divergent agent outcomes but do not by themselves diagnose inflation in a player-traded market. Exchange markets between players are deferred until their matching and conservation rules are separately specified.

## Units, nulls, and identifiers

- Currency and inventory values use exact integer base units unless a specific scale is declared.
- Every resource mutation has an action, source/sink category, and configuration revision.
- Purchases require affordability and prerequisites at the moment of transition.
- Reached and unreached milestones both contribute to cohort reporting.
- Simulated agent policies are assumptions and do not establish real player preferences.

An absent value, unknown value, invalid value, and numerical zero are distinct. Identifiers preserve source namespaces. Timestamps identify clock and precision. Collections specify whether their order is semantically significant. Statistical summaries specify population, filters, denominators, and time window. Serialization decisions must survive a cross-language round trip without precision loss.

## Storage and migration

Immutable source evidence is stored separately from derived views. A migration names source and destination versions, checks prerequisites, and produces a validation report. The prior accepted artifact remains available until the replacement passes its checks. Changes to meaning or units require a new schema major version. A path rename does not alter content identity; a corrected input changes lineage even when the filename is unchanged.

## Retention and portability

Keep manifests and compact diagnostics for accepted runs. Large raw inputs may live outside Git and carry availability and redistribution metadata. An export includes a relative artifact index and integrity digests, avoiding machine-specific absolute paths. Reports clearly identify missing or restricted inputs. User-generated or private information is included only in deliberately selected export scopes.
