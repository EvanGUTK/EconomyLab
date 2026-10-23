# EconomyLab — operations and recovery plan

## Initial operating model

Run large cohorts as bounded local batches with progress and cancellation between runs. Store verbose trajectories selectively while retaining compact summaries and seeds for all trials. A report must state which trajectories were sampled. Game exports target isolated test configurations before any production publishing.

## Startup protocol

Load and validate the effective configuration; record its digest. Verify schema compatibility, output permissions, free storage, and required source availability. Recover or quarantine incomplete prior work before accepting new commands. A startup failure identifies the failed prerequisite and leaves accepted artifacts untouched. Show the exact active environment and mode in diagnostics.

## Failure handling

Invalid or unbounded behavior stops with an action trace and configuration reference. A zero-cost repeatable source can create an infinite loop; validation and event-budget guards identify it explicitly. A missing telemetry mapping creates incomplete calibration, not a plausible fitted model. Exports cannot claim compatibility with unsupported game features.

## Persistence and backup

Configuration, immutable manifests, and accepted outputs have distinct lifecycles. Before adopting a backup as valid, restore it into a separate location and verify artifact digests and a representative result. Checkpoint frequency is a measured tradeoff between storage and recoverable work. The application never assumes a process supervisor or the browser session is a durable state store.

## Diagnostics and resource boundaries

Logs record run, input, and correlation IDs. Counters distinguish attempts, accepted work, duplicates, failures, and retries. Disk exhaustion has a defined stop condition. Large files live outside Git. Credentials and user-private artifacts are excluded from logs and public diagnostics. External-service adapters record their endpoint class, permission needs, quotas, and recovery policy when implemented.

## Release lifecycle

Build from a recorded revision, validate setup in a clean environment, run the domain acceptance scenarios, and create release notes that identify known limitations. Schema migrations require a tested reverse or restore path. A rollback preserves raw evidence and records which derived outputs require recomputation. Public issue reports should use synthetic reproductions where possible.
