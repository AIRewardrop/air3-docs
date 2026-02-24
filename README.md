# AIR3 Docs v2

AIR3 is the flagship AI agent of the AIRewardrop ecosystem and the utility hub for AIR3-powered products.

This documentation reflects the current product stack and protocol direction shown across:
- AIR3 public site
- AIRewardrop company hub
- AIRdApp product interfaces
- AIRTrading Engine / Pacifica execution design
- AIRTrack live testing and simulation workflows

## What AIR3 is

AIR3 is an always-on AI agent and MetaHuman live interface focused on crypto market intelligence:
- on-chain and market analysis
- social sentiment and trend monitoring
- real-time charts and reports
- autonomous posting and live interaction (X, Twitch, YouTube, Telegram, Discord)
- tokenized utility modules and partner-facing services

## Product stack at a glance

AIR3 is not only a chat agent. It is the front-end token and service layer for a broader stack:

- **AIRTrack**: tracking and simulation layer (no user fund execution)
- **AIRTrading**: execution layer for vetted strategies only
- **AIRSocial**: social missions / points / community activity
- **AIRSponsor**: buy + burn sponsor slots for AIR3 live visibility
- **AIRTool**: token-gated AIR3 agent rental for third-party Telegram/Discord communities

## Important distinction: AIRTrack vs AIRTrading

This is a core documentation rule and must stay explicit everywhere:

- **AIRTrack is tracking/simulation only**
  - Used to test strategies live
  - Turns AIR3 X posts / signals into simulated trades
  - Tracks positions, PnL, and rule-based risk adjustments
  - No user funds are executed there

- **AIRTrading is real execution**
  - Operates through the vault execution flow
  - Runs only strategies that have passed live testing on AIRTrack
  - Includes vault accounting, withdrawals, epoch settlement, and profit distribution logic

## Transparency model (on-chain + social)

AIR3 transparency is intentionally layered:
- **On-chain / protocol transparency** for accounting and settlement logic
- **Product transparency** via AIRdApp / AIRTrack dashboards and history
- **Social transparency** via trade posts on X (https://x.com/AIRewardrop): open post at entry, confirmation card at close with PnL

This makes it easier for users to verify that what they see in the product is also reflected in public social updates.

## Docs structure

Start here:
- [Quickstart](getting-started/quickstart.md)
- [Products Overview](products/overview.md)
- [AIRTrading Protocol Overview](protocol/overview.md)
- [Roadmap](roadmap/roadmap-2025-2027.md)
- [FAQ](resources/faq.md)

## Risk notice (user-friendly but real)

AIR3-related products include analytics, simulations, and protocol concepts for automated execution.
Trading and DeFi activity carry risk, including loss of capital, execution slippage, fees, and strategy underperformance.

This docs set currently describes an intended **no-leverage** AIRTrading operating model, so liquidation risk is not presented as a default user risk unless that changes in a future version.
