# Architecture and Auditability

AIR3 documentation describes a multi-layer transparency model designed to make protocol behavior and trade communication easier to verify.

## Transparency layers

### 1) Product interface transparency

AIRdApp and AIRTrack provide user-facing visibility into product modules, tracked trades, and performance views.

![AIRTrack Dashboard](../assets/images/airtrack-dashboard.png)
*Figure: AIRTrack dashboard showing live tracking, chart context, and simulated trade records used for strategy validation.*

*AIRTrack dashboard view used for strategy tracking, simulation visibility, and performance review.*

### 2) Social trade traceability

AIR3 publishes trade-related updates on X through the official AIRRewardrop account:
- https://x.com/AIRewardrop

Trade communication includes:
- a trade announcement at position opening
- a closing confirmation card with realized PnL
- a public timeline that can be cross-referenced with AIRdApp/AIRTrack context

![X Trade Traceability Example](../assets/images/x-trade-traceability-example.png)
*Figure: Example X post flow showing social trade traceability with entry announcement and closing confirmation card including realized PnL.*

*Example social trade traceability flow with closing confirmation card and realized PnL.*

### 3) Protocol and accounting transparency

The protocol section documents:
- vault share logic
- pro-rata withdrawal processing
- ExitTicket settlement flow
- epoch accounting and rewards split
- user exclusion rules that prevent double allocation

This makes the accounting model understandable before reading contract-level implementation details.

### 4) On-chain auditability (where deployed)

Where protocol smart contracts are deployed, on-chain events and balances provide an auditable record of key accounting actions and distribution flows.

The documentation describes expected event semantics and accounting behavior; deployed contract versions remain the source of truth for implementation-specific details.

## Architectural principle

AIR3 uses layered transparency rather than relying on a single interface:

- **social visibility** for public trade communication
- **product UI visibility** for operational tracking and user navigation
- **protocol documentation** for accounting logic
- **on-chain records** for verifiable execution and settlement state (where deployed)
