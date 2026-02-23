# Architecture and Auditability

## Why auditability matters here

AIRTrading combines:
- pooled user capital exposure
- dynamic strategy execution
- delayed withdrawals
- periodic profit distribution
- token conversion and split logic

Without auditability, users cannot verify fairness.

## Required auditability surface

The protocol should make it possible to verify, at minimum:

### Withdraw path
- user share at request time
- close ratio used
- pro-rata close behavior across all positions
- realized value
- PnL sign and amount
- exit ticket unlock time
- exclusion state activation time

### Epoch settlement path
- epoch start and end values
- realized profit/loss
- fee
- net split (buyback/users)
- active base used for distribution
- reward index updates

### Reward claims
- user index before/after claim
- claimable amount
- claim execution amount

## Operational transparency

Beyond on-chain events, off-chain execution transparency is highly recommended:
- order execution logs
- reduce-only confirmations
- slippage metrics
- error/retry telemetry
- epoch settlement reports

## AIRTrack as a transparency complement

AIRTrack improves ecosystem transparency by exposing live strategy behavior during simulation/testing, before execution strategies are promoted into AIRTrading.
