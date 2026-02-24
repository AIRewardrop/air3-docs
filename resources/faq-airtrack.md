# AIRTrack FAQ

## What is AIRTrack?

AIRTrack is the live tracking, simulation, and strategy validation layer in the AIR3 ecosystem. It monitors strategy behavior in live market conditions and records outcomes in a structured interface.

## Is AIRTrack real trade execution?

No. AIRTrack is not a real execution product. It is used to test and validate strategies through live tracking and simulation before any promotion to a real execution environment.

## Why is AIRTrack important if it does not execute trades?

AIRTrack is the quality and transparency layer for strategy development. It allows the team and users to observe strategy behavior, compare outcomes, review trade logic performance, and document results before real deployment decisions.

## How does AIRTrack relate to AIRTrading?

AIRTrack and AIRTrading are intentionally separated:
- **AIRTrack** = validation layer (tracking/simulation)
- **AIRTrading** = execution layer (real deployment)

Strategy workflow:
**idea/strategy -> live validation on AIRTrack -> promotion to AIRTrading only after passing live tests**

## How are AIRTrack trades surfaced to the public?

AIRTrack data is presented through AIRdApp/AIRTrack interfaces, which can include trade status, trade history, price levels, and PnL tracking views depending on the strategy/module. AIR3 also publishes social trade traceability updates on X for public visibility.

## Does AIRTrack use social signals?

AIRTrack can be used to model and validate strategies derived from social trend inputs, including agent-observed momentum and ticker mentions. The specific strategy logic and filters remain strategy-dependent.

## Can AIRTrack show profitable results while AIRTrading performs differently later?

Yes. AIRTrack validates behavior in observed conditions, but future execution outcomes can differ due to changing market conditions, fees, slippage, and execution timing. AIRTrack improves validation quality, but it does not eliminate trading risk.

## Does AIRTrack replace protocol documentation?

No. AIRTrack explains strategy testing and live tracking. The AIRTrading Vault model, withdrawal flow, and settlement logic are documented in the [Protocol](../protocol/whitepaper-index.md) section.
