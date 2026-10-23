# EconomyLab — interfaces and integration specification

All interfaces below are proposed contracts. Names describe responsibilities rather than installed APIs.

| Boundary | Request / input | Response / output | Guarantee |
| --- | --- | --- | --- |
| ValidateEconomy | EconomyConfig | Accepted graph or field diagnostics | No unresolved references |
| RunCohort | Config + policies + named seeds + horizon | SimulationManifest and event artifacts | Independent and reproducible run identity |
| CompareConfigs | Two accepted cohort manifests | Metrics, differences, uncertainty | Censoring and compatible observation windows visible |
| ExportGameConfig | Accepted config + adapter capability | Supported game config + mapping manifest | No silent dropping of unsupported mechanics |
| ImportTelemetry | Explicit event dataset + mapping | Calibration observations and coverage | No assumption of automatic platform-dashboard access |

## Domain-specific behavior

Roblox AnalyticsService economy events provide a source/sink vocabulary, but dashboard presence does not establish an external API for downloading all player-level behavior. The initial telemetry adapter should use deliberately collected test events or supported exports with permission and a defined privacy scope. A Shiftcraft adapter maps rewards and upgrade purchases; station queues and physical movement remain Shiftcraft responsibilities.

## Import and export rules

Imports validate schema version, domain units, source identity, completeness, payload hash, and declared capabilities. An unsupported optional capability is surfaced to the caller; mandatory capability gaps reject the request. Exporters include contract version and a provenance manifest, and must not require direct access to an internal database.

Request identities are stable across retries. Repeated completed requests return the recorded result or an explicit duplicate result; requests with an existing identity and different content are rejected. Timeouts distinguish a known rejection from an unknown external outcome. Consumers cannot infer that an action did not happen merely because a response was lost.

## Shared conventions

Use [CONTRACTS.md](CONTRACTS.md) for envelope, time, precision, and compatibility conventions. File-based interoperability is the first integration target. Binary or local process protocols can follow after a measured need and a conformance test. A contract's ownership is recorded in [ECOSYSTEM.md](ECOSYSTEM.md).

## Consumer conformance checklist

The future adapter must demonstrate valid import, unsupported-version rejection, precision-preserving round trip, duplicate handling, corrupt-artifact rejection, and recovery from a truncated output. This checklist specifies future evidence; it does not assert that an adapter already exists.
