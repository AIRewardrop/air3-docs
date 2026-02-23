# User Commands (AIR3 Engine)

This page summarizes the AIR3 command experience and public-facing capability set described in the AIRewardrop User Manual (AIR3 V4 Engine).

## AIR3 engine positioning

AIR3 is presented as:
- a 24/7 market analyst
- AI-driven and live-interactive
- backed by a hyper-realistic MetaHuman avatar
- focused on fast insights and transparent growth

## Key feature themes (Engine V4)

The public manual describes features such as:
- Boosted Token Scanners
- Real-time Prices
- Ready-to-use Technical Charts
- Instant Fundamental Snapshots
- Deep Asset & Trend Analysis
- Trending & Social Mentions
- Live Market Sentiment
- Breaking News Feed
- Fresh Listings Detector
- Capital Flow & Volume Heatmap
- Dashboards

## Basic query syntax (X / Twitter)

AIR3 command usage is based on tagging the account and adding an action word plus a ticker or contract address.

Examples:
- `@AIRewardrop chart $CRV 1h`
- `@AIRewardrop fundamental $XRP`
- `@AIRewardrop analysis 0x...`

Common action words include:
- `chart`
- `analysis`
- `price`
- `sentiment`
- `news`
- `audit`
- `fundamental`
- `rise in mention`
- `most mentioned`

## Common command patterns

### Chart by ticker
- `@AIRewardrop chart $TICKER`

### Chart by contract
- `@AIRewardrop chart <contract_address>`

### Analysis by ticker
- `@AIRewardrop analysis $TICKER`

### Price lookup
- `@AIRewardrop price $TICKER`

### Sentiment lookup
- `@AIRewardrop sentiment $TICKER`

### News lookup
- `@AIRewardrop news $TICKER`

## Product transition note from the public manual

The public manual already points toward the dApp rollout and AIRtrak as the first verifiable trading module.

This docs pack extends that with the current product split:
- **AIRTrack** = tracking/simulation and live strategy testing
- **AIRTrading** = execution for strategies that pass AIRTrack testing
- **AIRSponsor / AIRTool / AIRSocial** = utility and ecosystem modules inside AIRdApp
