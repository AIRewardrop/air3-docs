# AIR3 Documentation

AIR3 is the public documentation hub for the AIRewardrop ecosystem.

It documents the AIR3 agent experience, AIRdApp product surface, AIRTrack strategy validation, AIRTrading protocol logic, AIR3 token utility, and the operating rules used to provide transparent user-facing products.

## What AIR3 includes

- **AIR3 Agent**: AI-native crypto agent experience across social and community channels.
- **AIRdApp**: product interface where users can access AIR ecosystem modules.
- **AIRTrack**: live tracking and simulation environment used to validate strategies on real market data and social momentum signals.
- **AIRTrading**: real execution layer where strategies may be deployed only after passing live validation on AIRTrack.
- **AIRSocial / AIRSponsor / AIRTool**: utility modules that expand AIR3 usage through community, sponsorship, and agent rental features.
- **AIR3 Token Utility**: buy-and-burn mechanisms, rewards, and ecosystem access flows.

## Core operating principles

### 1) AIRTrack and AIRTrading are not the same product

AIRTrack is a **tracking, simulation, and validation layer**. It models entries and exits, tracks PnL, and records strategy behavior in a live environment. It does **not** execute real trades.

AIRTrading is the **real execution environment**. It is the deployment layer for strategies that have already passed live validation requirements on AIRTrack.

**Strategy lifecycle**  
Idea -> live validation on AIRTrack -> promotion to AIRTrading after passing live tests

### 2) Transparent trade traceability

AIR3 combines **social transparency** and **protocol/accounting transparency**.

- Trade announcements are posted on X at position opening: https://x.com/AIRewardrop
- A closing confirmation card is posted when the trade closes, including realized PnL
- AIRdApp and AIRTrack provide historical tracking and operational context
- Protocol documentation defines auditable accounting flows for vault exits and epoch settlement

![AIRdApp Home](assets/images/airdapp-home.png)

*AIRdApp product hub with modular access to AIRTrack, AIRTrading, AIRSocial, AIRSponsor, and AIRTool.*

## AIRTrading Engine at a glance

The AIRTrading Engine uses a single vault model with percentage-based user shares. A withdrawal request closes the same percentage of **all** open positions pro-rata, creates an exit balance, and settles through a fixed 7-day delay via an ExitTicket.

![AIRTrading Engine Diagram](assets/images/airtrading-engine-diagram.png)

*High-level AIRTrading Engine architecture showing vault routing, strategy execution, profit splitting, buyback, and user rewards.*

## Where to start

- New readers: [Quickstart](getting-started/quickstart.md)
- Product overview: [Products Overview](products/overview.md)
- Protocol logic: [Protocol Overview](protocol/overview.md)
- Frequently asked questions: [FAQ](resources/faq.md)
- Official links: [Official Links](resources/official-links.md)
