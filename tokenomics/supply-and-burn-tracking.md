# Supply, Burns, and Reporting

This page documents the AIR3 supply framework and the reporting approach used in public-facing documentation.

## Supply Baseline

- **Initial launch supply:** `1,000,000,000 AIR3` (fair launch)
- **Network:** Solana
- **Token mint (CA):** `2jvsWRkT17ofmv9pkW7ofqAFWSCNyJYdykJ7kPKbmoon`

## Reporting Method

For AIR3, the most useful public supply view is:

**Effective circulating profile = launch supply - burned tokens (plus any implementation-specific exclusions if disclosed).**

In practice, users should verify current values through public dashboards and explorers because these values change over time.

## Burns

AIR3 documentation tracks burns through publicly verifiable on-chain references (burn address and explorer links).

### Burn tracking reference
- [Solscan token page (AIR3)](https://solscan.io/token/2jvsWRkT17ofmv9pkW7ofqAFWSCNyJYdykJ7kPKbmoon)
- [Burn address (Solana incinerator)](https://solscan.io/account/1nc1nerator11111111111111111111111111111111)

## Current snapshot example (replaceable, timestamped)

The docs may show a timestamped snapshot for user convenience, while the explorer/dashboard remains the source of truth for live values.

Example snapshot (from user-provided market dashboard image):
- **Total supply:** `969.25M AIR3`
- **Circulating supply:** `969.25M AIR3`
- **Holders:** `446`
- **Market cap (snapshot):** `$119.81K`

This implies that more than 3% of the initial 1B supply has been burned (exact burn total should always be checked on-chain at the time of reading).

## Dev Wallet Disclosure (public docs wording)

Where the team discloses a dev wallet balance (for example, ~19.65M AIR3 in current documentation discussions), it should be reported as:
- a **wallet balance disclosure**
- not a substitute for explorer-based supply calculations
- subject to change over time

Use precise timestamps when publishing wallet balance figures in docs or announcements.

## Documentation policy for live values

To keep the docs professional and accurate:
- Use narrative explanations in the main tokenomics pages.
- Link users to the live dashboards for current values.
- If publishing numeric snapshots, label them clearly with date/time and data source.
