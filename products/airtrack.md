# AIRTrack (Tracking & Simulation Only)

AIRTrack is the live testing and transparency layer for AIR3 strategies.

This page is intentionally explicit:

## AIRTrack is not execution

AIRTrack does **not** execute user funds and is **not** the vault execution engine.

AIRTrack is used to:
- test new strategies live
- simulate trades from AIR3 agent outputs/posts/signals
- track entries, exits, active/pending/closed states
- measure realized and unrealized PnL
- observe strategy behavior over time on a broad ticker universe
- validate whether a strategy is good enough to be promoted to AIRTrading

## Core function

AIRTrack is a simulation layer that monitors the most mentioned and most increased tickers the AIR3 agent verifies on X, then models trade entries from real-time social trends.

It is built to cover the widest possible ticker universe by leveraging X trend momentum and AIR3 signal generation.

In practical terms:
- AIR3 posts or verified signals can spawn simulated positions
- positions are tracked live
- PnL is updated and logged
- all moves are visible in one dashboard

## Strategy testing pipeline role

AIRTrack is the staging ground for strategy validation.

The expected pipeline is:
1. Strategy idea is defined
2. Strategy runs in AIRTrack live simulation
3. Performance and stability are reviewed
4. Risk behavior is reviewed (including stop logic)
5. Only passing strategies are exported to AIRTrading execution

## Rule-based risk management in AIRTrack

AIRTrack can test rule-based TP/SL management, including dynamic stop tightening as price approaches target.

Example principle:
- as progress toward TP increases
- stop loss is moved up to lock in profit
- strategy behavior is recorded and observable in the dashboard

This makes AIRTrack useful not only for performance reporting, but also for strategy QA.

## Social traceability (X) + dashboard traceability

AIR3 adds a second transparency layer beyond the dashboard itself.

For tracked strategies and agent-driven trade narratives:
- trade openings are posted on X (https://x.com/AIRewardrop)
- trade closures are posted with a confirmation card and realized PnL
- users can cross-check social posts with AIRdApp / AIRTrack history

This gives the ecosystem both:
- **dashboard transparency** (trade lifecycle and PnL tracking)
- **social transparency** (timestamped public posts on X)

## UI reference

![AIRTrack Dashboard](../assets/images/airtrack-dashboard.png)

The dashboard shows:
- active / pending positions
- chart context
- entry / TP / SL levels
- realized PnL stats
- closed trades history
- filters and time windows

## X trade post example (social traceability)

![AIR3 X Trade Post Example](../assets/images/x-trade-traceability-example.png)

Example workflow:
- post at trade open on X
- monitor in AIRTrack / AIRdApp
- post close confirmation card with realized PnL on X

## Why this separation matters

Separating tracking from execution improves:
- transparency
- strategy QA
- user trust
- risk discipline

AIRTrack proves behavior. AIRTrading executes only what has passed.
