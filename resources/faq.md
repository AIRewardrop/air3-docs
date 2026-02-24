# FAQ

## What is the difference between AIRTrack and AIRTrading?

AIRTrack is the live **tracking, simulation, and strategy validation layer**. It tracks and evaluates strategy behavior in live conditions, but it does not execute real trades.

AIRTrading is the **real execution environment**. Strategies are promoted to AIRTrading only after they pass live validation requirements on AIRTrack.

## Are all trades executed directly from AIRTrack?

No. AIRTrack is not the execution engine. AIRTrack is used to observe and validate strategy behavior before deployment decisions are made.

## How are trades made transparent to users?

AIR3 uses a layered transparency model:

- trade announcements on X when positions open
- trade close confirmation cards with realized PnL on X
- AIRdApp / AIRTrack tracking views for historical context
- protocol documentation and on-chain accounting transparency where applicable

Official X account:
- https://x.com/AIRewardrop

## How does user withdrawal work in the AIRTrading vault model?

When a user requests withdrawal, the protocol determines the user's current share of total vault value and closes the same percentage of all open positions pro-rata. The realized value becomes the user's exit balance, an ExitTicket is created, and funds become claimable after a fixed 7-day delay.

The user is excluded immediately from further PnL exposure and epoch reward distributions once the withdrawal request is accepted.

## Does the protocol use leverage?

The intended operating model documented in this version is no leverage. User-facing risk communication therefore focuses on market moves, slippage, execution timing, fees, and strategy underperformance.

## What happens if many users request withdrawal at the same time?

The same pro-rata rule applies. The vault reduces the same aggregate percentage across open positions, creates exit balances for requesting users, and excludes them from further PnL and epoch rewards. Operationally, this can increase execution complexity and slippage, but the accounting rule remains consistent.

## Where can I read the protocol logic?

Start with:
- [Protocol Overview](../protocol/overview.md)
- [Withdraw Flow (7-Day Delay)](../protocol/withdraw-flow.md)
- [Seasons and Epochs](../protocol/seasons-and-epochs.md)
- [Risk Management](../protocol/risk-management.md)
