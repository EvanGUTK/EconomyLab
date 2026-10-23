# EconomyLab — primary source register

Prepared 2026-10-23. References inform the proposal; upstream capabilities, entitlements, quotas, and versions must be rechecked when implementing an adapter. External documentation is not proof that this repository implements an integration.

| Primary reference | Design relevance |
| --- | --- |
| [Roblox economy events](https://create.roblox.com/docs/production/analytics/economy-events) | Source and sink event semantics |
| [Roblox analytics event types](https://create.roblox.com/docs/production/analytics/event-types) | Economy, funnel, and custom event categories |
| [NumPy random generation](https://numpy.org/doc/stable/reference/random/index.html) | Candidate seeded stochastic simulation foundation |

## Implementation verification tasks

Check Roblox AnalyticsService event restrictions, server-side requirements, quotas, and supported data-access paths. Verify RNG behavior and parallel seed derivation with selected NumPy versions. No automatic raw analytics export capability is assumed.

## Evidence classification

Protocol or platform facts come from the linked primary documentation. Architecture, scope, component names, interface designs, and milestones are original proposals for this project. Future empirical claims must link their own input manifests and measurements. Do not copy provider examples, redistributable-looking data, or game art into the repository without checking the applicable license and attribution requirements.
