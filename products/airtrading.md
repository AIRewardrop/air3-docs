# AIRTrading

AIRTrading is the **real execution environment** of the AIR ecosystem.

It is the strategy deployment layer used for validated strategies that have already passed live testing and observation on AIRTrack.

## What AIRTrading is

AIRTrading is:

- a **real execution layer**
- a **strategy deployment environment**
- a **vault-based accounting and distribution system**
- a **protocol-facing product integrated with AIR3 token utility**

AIRTrading is not the simulation layer. Strategy testing and validation occur in AIRTrack before promotion.

## Strategy admission path

Only strategies that pass live validation on AIRTrack are eligible for deployment into AIRTrading.

**Operational pipeline**
Idea -> AIRTrack live validation -> review -> AIRTrading deployment

This separation keeps the execution layer focused on vetted strategy logic.

## Vault-based operating model

AIRTrading uses a single vault model in which users hold a percentage share of total vault value. Withdrawals are handled using a pro-rata close of all open positions for the requesting user share, followed by a fixed 7-day settlement delay.

See:
- [Vault Model](../protocol/vault-model.md)
- [Withdraw Flow (7-Day Delay)](../protocol/withdraw-flow.md)
- [Seasons and Epochs](../protocol/seasons-and-epochs.md)

## Execution venue

AIRTrading execution is designed around Pacifica as the execution venue for perpetual strategy operations.

See:
- [Pacifica Execution Layer](../protocol/pacifica-execution-layer.md)

## Transparency and reporting

AIRTrading is documented with two complementary visibility layers:

1. **Protocol/accounting transparency** (vault shares, exits, settlement rules, rewards logic)
2. **Social trade traceability** (trade-open and trade-close posts on X, with realized PnL confirmation cards)

![AIRTrading Engine Diagram](../assets/images/airtrading-engine-diagram.png)
*Figure: AIRTrading Engine high-level flow showing vault routing, strategy execution, profit splitting, and AIR3 buyback/user reward distribution.*

*AIRTrading Engine high-level flow: deposits, vault execution, profit split, buyback, and user rewards.*
