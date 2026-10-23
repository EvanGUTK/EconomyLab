# EconomyLab — architecture decision register

Status meanings: **proposed** is the current blueprint choice; **open** needs a bounded experiment before implementation. No choice here proves runtime behavior.

| ID | Status | Decision | Alternative / consequence |
| --- | --- | --- | --- |
| ADR-001 | Proposed | Discrete events before rendered simulation | Improves inspectability for economy timing; physical gameplay stays external |
| ADR-002 | Proposed | Explicit agents instead of learned behavior initially | Transparent assumptions enable hand-solved validation |
| ADR-003 | Proposed | Censored outcomes remain visible | Avoids misleading survivor-only progression statistics |
| ADR-004 | Proposed | Narrow game adapters | No universal interpreter for Roblox scripts |

## Open questions and resolution method

- **Which first game economy provides a realistic but bounded example?** Resolve with a minimal fixture, an explicit requirement, or a recorded compatibility check before expanding the corresponding milestone.
- **What observation window and session policies reflect the intended test?** Resolve with a minimal fixture, an explicit requirement, or a recorded compatibility check before expanding the corresponding milestone.
- **Which playtest events can be collected with appropriate permissions and privacy boundaries?** Resolve with a minimal fixture, an explicit requirement, or a recorded compatibility check before expanding the corresponding milestone.

## Change protocol

Each new decision records context, considered alternatives, selected option, downside, acceptance evidence, and the condition that would trigger reconsideration. Superseded decisions remain in the register. A rejected alternative is recorded only when it explains a continuing tradeoff. Review decisions at milestone boundaries rather than changing foundational contracts incidentally during UI work.
