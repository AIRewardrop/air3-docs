# Pacifica Execution Layer

AIRTrading documentation assumes execution on Pacifica perpetuals.

This page documents the integration boundary and the operational topics that matter for AIRTrading design.

## Scope

Pacifica is the trading venue for:
- perpetual position execution
- margin and leverage behavior
- mark-to-market PnL
- liquidation rules
- fees and funding mechanics
- API-based order execution (if using API executor)

Pacifica's trading docs currently describe support for 35+ perpetual assets, both cross and isolated margin, and market-dependent leverage ranges. Venue rules, limits, and supported assets can change, so Pacifica documentation remains the source of truth.

## Trading access / jurisdiction note

Pacifica documentation includes restricted-jurisdiction limitations for trading access. AIRTrading integrations must respect venue restrictions and compliance constraints.

## API execution note

Pacifica provides REST API, WebSocket, signing, and rate-limit documentation. Executor implementations should be built against the current Pacifica API docs and endpoints.

## Protocol design implications of Pacifica

### Margin and leverage
Vault risk management must be compatible with Pacifica margin and leverage behavior:
- leverage cap
- margin mode choices
- maintenance margin awareness
- buffer preservation during unwinds

### Liquidation mechanics
Mass withdrawals and rapid deleveraging can increase liquidation risk if the vault is thinly margined and the market moves during execution.

### Mark price and oracle behavior
PnL and liquidation thresholds depend on venue pricing logic (oracle/mark price), not only last trade price.

### Fees and funding
Maker/taker fees and funding affect net vault results and should be included in PnL accounting and strategy evaluation.

### API constraints
Executor implementations must consider:
- rate limits
- request signing
- order pacing
- retry logic
- deterministic logging for auditability

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
- https://docs.pacifica.fi

Trading:
- https://docs.pacifica.fi/trading-on-pacifica/overview
- https://docs.pacifica.fi/trading-on-pacifica/margin-and-leverage
- https://docs.pacifica.fi/trading-on-pacifica/liquidations
- https://docs.pacifica.fi/trading-on-pacifica/funding-rates
- https://docs.pacifica.fi/trading-on-pacifica/trading-fees
- https://docs.pacifica.fi/trading-on-pacifica/contract-specifications/oracle-price-and-mark-price
- https://docs.pacifica.fi/trading-on-pacifica/fund-security
- https://docs.pacifica.fi/trading-on-pacifica/deposits-and-withdrawals

API:
- https://docs.pacifica.fi/api-documentation/api/rest-api
- https://docs.pacifica.fi/api-documentation/api/signing
- https://docs.pacifica.fi/api-documentation/api/rate-limits
- https://docs.pacifica.fi/api-documentation/api/websocket

Programs:
- https://docs.pacifica.fi/builder-program

## Documentation note

Venue-specific details can change. Pacifica docs are the source of truth for current execution rules, fees, API behavior, and restrictions.
