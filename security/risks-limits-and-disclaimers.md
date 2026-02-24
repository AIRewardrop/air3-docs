# Risks, Limits, and Disclaimers

This page summarizes key user-facing risks, operating limits, and implementation boundaries for AIR3 products and the AIRTrading protocol.

## General product and protocol boundaries

- Documentation describes product behavior and protocol logic at a functional level.
- Some details are implementation-specific and may vary by deployed version.
- Deployed contracts, product interfaces, and official announcements are the source of truth for live behavior.

## AIRTrack vs AIRTrading (important distinction)

- **AIRTrack** is a tracking, simulation, and strategy validation product.
- **AIRTrack does not execute real trades.**
- **AIRTrading** is the real execution environment for strategies that pass validation requirements.

Users should not interpret AIRTrack simulation outcomes as guaranteed AIRTrading results.

## Primary user-facing risks (no-leverage intended operating model)

The intended operating model documented in this docs set is no leverage. The primary risks presented to users are therefore:

- adverse market moves
- slippage
- execution timing differences
- fees and venue costs
- strategy underperformance
- temporary processing delays under stressed conditions

These risks are explained in more detail in the protocol risk management section.

## Operational limits

Depending on deployment version and venue conditions, the system may apply operational limits or safeguards such as:

- staged execution procedures
- strategy capacity limits
- temporary pauses for maintenance or upgrades
- claim timing rules and settlement windows
- product availability changes by module

## No guarantee language

- Past results, tracked outcomes, and simulations do not guarantee future performance.
- Strategy validation improves selection quality but does not eliminate market risk.
- Public trade traceability improves transparency but does not change execution risk.

## References

- [Risk Management](../protocol/risk-management.md)
- [Pacifica Execution Layer](../protocol/pacifica-execution-layer.md)
- [Official Links](../resources/official-links.md)
