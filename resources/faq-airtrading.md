# AIRTrading FAQ

## What is AIRTrading?

AIRTrading is the real execution environment in the AIR3 ecosystem. It is the deployment layer where strategies that have passed live validation on AIRTrack can be executed in a production trading workflow.

## Does AIRTrading execute every strategy shown on AIRTrack?

No. AIRTrack is a validation layer. Only strategies that pass live testing and internal deployment criteria are considered for promotion to AIRTrading.

## What is the Vault model in simple terms?

AIRTrading uses a single Vault portfolio model with open positions. Each user holds a share of the Vault based on the value of their quota relative to total Vault value.

## How does a withdrawal request work?

When a user submits a withdrawal request:
1. The user share is calculated at request time.
2. The Vault closes the same pro-rata percentage of all open positions.
3. The protocol creates an ExitTicket with the user settlement values.
4. Funds become claimable after a fixed 7-day delay.

During the delay, the user is no longer exposed to ongoing Vault PnL because the user allocation has already been separated from active exposure.

## Is the user still included in the current Epoch after a withdrawal request?

No. The withdrawal effect is immediate for accounting and exposure purposes. Once the ExitTicket is created and the user is excluded, that user no longer participates in the current Epoch distribution or subsequent Epochs.

## What is an ExitTicket?

An ExitTicket is the user settlement record created after the protocol closes the user’s pro-rata share of positions. It records the realized exit value, PnL outcome, and unlock time for claim.

## What is “realized value” in the withdrawal flow?

Realized value is the stable-value amount obtained by closing the user’s pro-rata share of the Vault positions at withdrawal request time. It is the basis for user settlement after the delay period.

## What happens if the user exits with a positive PnL?

If the user’s realized PnL is positive, the protocol applies the configured profit handling logic, including AIR3 conversion and the configured split (for example buyback and user rewards components) after applicable fees.

## What happens if the user exits with a negative PnL?

A negative PnL is absorbed by the user allocation. In that case, the realized value is lower than the principal basis, and the user receives the reduced exit value after the delay.

## How are rewards handled at the end of an Epoch?

At Epoch settlement, the protocol accounts for realized PnL in stable value. If net PnL is positive, the configured split is applied to AIR3-related reward and buyback flows after fees. Distribution logic uses the active user base only (excluding users already exited via withdrawal request).

## Does AIRTrading use leverage?

The documented operating model is a no-leverage intended operating model. User-facing risk discussions focus on market moves, slippage, execution timing, fees, and strategy underperformance rather than leverage-driven liquidation mechanics.

## Where can I read the full protocol logic?

See the [Protocol Whitepaper Index](../protocol/whitepaper-index.md), especially:
- [Vault Model](../protocol/vault-model.md)
- [Withdraw Flow](../protocol/withdraw-flow.md)
- [Seasons and Epochs](../protocol/seasons-and-epochs.md)
- [Rewards and Buyback](../protocol/rewards-and-buyback.md)
- [Risk Management](../protocol/risk-management.md)
