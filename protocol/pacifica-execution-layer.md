# Pacifica Execution Layer

AIRTrading documentation assumes execution on Pacifica.

This page documents the integration boundary and the operational topics that matter for AIRTrading design.

## Scope

Pacifica is the execution venue for AIRTrading.
The venue defines execution behavior, fees, supported instruments, APIs, and operational constraints used by the strategy executor.

Pacifica documentation describes venue mechanics and APIs. Venue rules, limits, and supported assets can change, so Pacifica documentation remains the source of truth.

## Important implementation note for AIR3 docs

This docs set does **not** assume leveraged operation as the default AIRTrading user model.

That means:
- Pacifica is used as the execution venue
- but AIR3 protocol/user docs should focus primarily on execution quality, fees, slippage, and operational reliability
- leverage / liquidation mechanics remain venue knowledge and future-compatible references, not the primary risk framing for the intended no-leverage rollout

## Trading access / jurisdiction note

Pacifica documentation includes restricted-jurisdiction limitations for trading access. AIRTrading integrations must respect venue restrictions and compliance constraints.

## API execution note

Pacifica provides REST API, WebSocket, signing, and rate-limit documentation. Executor implementations should be built against the current Pacifica API docs and endpoints.

## Protocol design implications of Pacifica

### Execution quality and order handling
Vault outcomes depend on:
- order placement quality
- reduce-only handling during exits
- slippage controls
- order pacing and retries

### Fees and venue costs
Trading fees and other venue-level costs affect net vault results and should be included in strategy evaluation and accounting.

### API constraints
Executor implementations must consider:
- rate limits
- request signing
- order pacing
- retry logic
- deterministic logging for auditability

### Venue mechanics (reference)
Pacifica docs also include margin/leverage, liquidation, and mark/oracle mechanics.
These links are retained for completeness and future compatibility, but they are not the primary user risk explanation for the intended no-leverage deployment model.

## Recommended implementation boundaries

### On-chain / protocol side
Should record:
- requested close ratio
- realized output
- user exclusion state
- epoch settlement results

### Off-chain executor side
Should manage:
- order placement and reduction sequencing
- reduce-only enforcement
- slippage controls
- retry and failure handling
- execution telemetry and logs

## Pacifica documentation links

Core docs:
- <https://docs.pacifica.fi>

Trading:
- <https://docs.pacifica.fi/trading-on-pacifica/overview>
- <https://docs.pacifica.fi/trading-on-pacifica/margin-and-leverage>
- <https://docs.pacifica.fi/trading-on-pacifica/liquidations>
- <https://docs.pacifica.fi/trading-on-pacifica/funding-rates>
- <https://docs.pacifica.fi/trading-on-pacifica/trading-fees>
- <https://docs.pacifica.fi/trading-on-pacifica/contract-specifications/oracle-price-and-mark-price>
- <https://docs.pacifica.fi/trading-on-pacifica/fund-security>
- <https://docs.pacifica.fi/trading-on-pacifica/deposits-and-withdrawals>

API:
- <https://docs.pacifica.fi/api-documentation/api/rest-api>
- <https://docs.pacifica.fi/api-documentation/api/signing>
- <https://docs.pacifica.fi/api-documentation/api/rate-limits>
- <https://docs.pacifica.fi/api-documentation/api/websocket>

Programs:
- <https://docs.pacifica.fi/builder-program>

## Documentation note

Venue-specific details can change. Pacifica docs are the source of truth for current execution rules, fees, API behavior, and restrictions.
