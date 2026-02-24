# Protocol Overview

The AIRTrading protocol defines the accounting and settlement logic used by the AIRTrading Engine.

This section describes the vault model, user share calculations, withdrawal flow, ExitTicket mechanics, epoch accounting, and AIR3 reward/buyback distribution logic in a clear and auditable format.

## Scope

This protocol documentation describes the operating logic and accounting model used by the AIRTrading Engine. Specific implementation details may vary by deployed contract version and are implementation-specific unless explicitly stated.

## Core protocol principles

1. **Single vault portfolio**
   - The vault is a single portfolio with open positions.
   - Each user owns a percentage share of total vault value.

2. **Pro-rata withdrawal logic**
   - A withdrawal request closes the same percentage of all open positions.
   - The user exit value is based on the value actually realized from that pro-rata close.

3. **Delayed settlement with immediate exposure stop**
   - A withdrawal request creates an ExitTicket with a fixed 7-day delay.
   - The user is excluded immediately from subsequent PnL exposure and epoch distributions.

4. **Epoch-based profit accounting**
   - Epoch PnL is realized in stable at settlement time.
   - Positive net profit is converted to AIR3 and split between buyback and user rewards after fees.

5. **Transparency by design**
   - Product UI visibility through AIRdApp and AIRTrack
   - Social trade traceability on X (@AIRewardrop)
   - Protocol and on-chain auditability where deployed

## Operating posture

The intended operating model documented in this section is **no leverage**. User-facing risk communication therefore focuses on the primary risks relevant to that posture, such as market moves, slippage, execution timing, fees, and strategy underperformance.

## Diagram

![AIRTrading Engine Diagram](../assets/images/airtrading-engine-diagram.png)

*Reference architecture for the AIRTrading Engine and profit distribution flow.*

## Reading order

- [Vault Model](vault-model.md)
- [Withdraw Flow (7-Day Delay)](withdraw-flow.md)
- [Seasons and Epochs](seasons-and-epochs.md)
- [Rewards and Buyback](rewards-and-buyback.md)
- [Risk Management](risk-management.md)
- [Pacifica Execution Layer](pacifica-execution-layer.md)
- [Worked Examples](worked-examples.md)
