# Products Overview

AIRewardrop is a modular product ecosystem built around the AIR3 token and the AIR3 agent.

The documentation separates products by function so users can understand what each module does and how they connect operationally.

## Product map

- **AIR3 Agent**: the agent interface and public-facing AI experience
- **AIRTrack**: live trade tracking, simulation, and strategy validation
- **AIRTrading**: real execution layer for validated strategies
- **AIRSocial**: community missions and points infrastructure
- **AIRSponsor**: live sponsor slot product using a buy-and-burn flow
- **AIRTool**: AIR3 agent rental for third-party Discord/Telegram communities
- **AIRdApp**: the application surface where these modules are accessed

![AIRdApp Home](../assets/images/airdapp-home.png)
*Figure: AIRdApp home interface showing the unified entry point for AIR3 modules and community access links.*

*AIRdApp home interface showing the AIR product modules and navigation structure.*

## Validation-to-execution pipeline

AIRTrack and AIRTrading are intentionally separated.

- AIRTrack is used to test and observe strategy behavior in a live environment
- AIRTrading is used to execute approved strategies in the real execution environment
- Strategies move from AIRTrack to AIRTrading only after passing live validation criteria

This separation improves operational clarity, user communication, and product trust.

## Transparency model across products

AIR3 uses multiple transparency layers:

1. **Product UI transparency** through AIRdApp and AIRTrack dashboards
2. **Social traceability** through trade open and close posts on X
3. **Protocol/accounting transparency** through documented vault and settlement logic
4. **On-chain verifiability** where protocol events and balances are exposed by deployed contracts

## Product pages

- [AIR3 Agent](air3-agent.md)
- [AIRTrack (Tracking & Simulation)](airtrack.md)
- [AIRTrading (Execution Layer)](airtrading.md)
- [AIRSocial](airsocial.md)
- [AIRSponsor](airsponsor.md)
- [AIRTool](airtool.md)
