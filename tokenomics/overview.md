# Tokenomics Overview

AIR3 is the native token of the AIR3 / AIRewardrop ecosystem on Solana.  
Its tokenomics are designed to connect product usage, protocol activity, and long-term ecosystem funding into a transparent operating model.

## Launch Model

AIR3 was launched as a fair launch on Moonshot (now Moonit) on Solana, with an initial total supply of **1,000,000,000 AIR3** at launch.

The launch path used Meteora liquidity infrastructure (including the Moonshot / Meteora launch flow), which is relevant for understanding early liquidity structure and fee mechanics.

## Tokenomics Design Principles

### 1) Utility-first positioning
AIR3 is tied to product usage across the AIR3 ecosystem (agent access, sponsorship surfaces, tools, and protocol-linked flows), rather than being documented as a passive claim on protocol revenue.

### 2) Transparent public references
Core token data is discoverable through public market dashboards and explorers, with official links maintained in the documentation.

### 3) Burn-aware supply reporting
The effective circulating profile should be read as a function of:
- initial launched supply
- tokens burned over time
- current balances of publicly identified wallets (where disclosed)

### 4) Product-funded treasury growth
A key design goal is to support a more self-sustaining operating model over time.  
In the AIRTrading protocol design, treasury funding for ecosystem growth and marketing is intended to be supported by protocol activity (including the configured share of net positive PnL after fees), rather than relying only on external financing.

## Relationship to AIRTrack and AIRTrading

- **AIRTrack** is a tracking and live simulation layer used to validate strategies and monitor outcomes.
- **AIRTrading** is the real execution environment, where only strategies that pass live testing on AIRTrack are eligible for deployment.

This distinction matters for tokenomics communication:
- AIRTrack improves strategy validation and transparency.
- AIRTrading is the execution layer tied to protocol accounting flows (including the buyback/users split model documented in the Protocol section).

## Where to find current data

For current market metrics, liquidity, and explorer data, see:
- [Market Structure and Liquidity](market-and-liquidity.md)
- [Supply, Burns, and Reporting](supply-and-burn-tracking.md)
- [Contracts and Addresses](contracts-and-addresses.md)
- [Official Links](../resources/official-links.md)
