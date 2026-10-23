# Simulation and calibration protocol

## Model declaration

An experiment specifies economy config, agent policy, session schedule, observation horizon, stopping rules, and named random streams. Record which observations an agent can use. An optimizer with perfect future knowledge is a stress-test policy, not a representative player.

## Analytical baseline

Before stochastic cohorts, solve a deterministic economy by hand: reward cadence, first purchase time, post-upgrade reward, session interruption, and final balance. Compare each event and exact amount. Then introduce one random mechanism at a time and check its sampling and conservation behavior.

## Comparisons

Use paired scenarios where common randomness remains meaningful. Structural changes can alter event counts and consume random values differently; independent named streams reduce accidental coupling. Report sensitivity across policies and seeds rather than selecting the best-looking trajectory.

## Progression statistics

For every milestone, show observation window, reached count, unreached count, completion fraction, and an explicitly described timing summary. Preserve censored outcomes. Resource reports show sources, sinks, balance changes, and unexplained residuals. A configuration is not better merely because one average falls.

## Calibration

Compare observed action rates, session lengths, purchases, and resource flows with simulated distributions using a declared telemetry mapping. Model disagreement is a useful result. Revise an agent policy as a new version and reevaluate previously selected conclusions. Do not infer causal retention improvements from a better fit to one historical playtest.
