# AIRTrading (Execution Layer)

AIRTrading is the execution product of the AIR ecosystem.

It is separate from AIRTrack by design:

- **AIRTrack = tracking and live simulation**
- **AIRTrading = real execution of vetted strategies**

## What AIRTrading does

AIRTrading handles:
- strategy execution on the chosen venue (Pacifica perpetuals)
- vault accounting
- user deposit/withdraw lifecycle
- delayed withdrawals with immediate exposure stop
- season/epoch PnL realization and distribution
- AIR3 buyback + user rewards split

## Strategy admission rule (recommended)

A strategy should be promoted to AIRTrading only if it has passed AIRTrack live testing based on criteria such as:
- sufficient sample size
- stable execution logic
- controlled drawdown behavior
- coherent TP/SL and trailing logic
- acceptable slippage assumptions under target market conditions

## Execution venue

Current design documentation assumes execution on Pacifica perpetuals.
See [Pacifica Execution Layer](../protocol/pacifica-execution-layer.md).

## Vault-based model

AIRTrading uses a single shared vault portfolio model:
- users own a percentage of the vault
- withdrawals are pro-rata across all open positions
- users are excluded from further PnL immediately at withdraw request
- payout happens after the fixed delay

See:
- [Vault Model](../protocol/vault-model.md)
- [Withdraw Flow (7d Delay)](../protocol/withdraw-flow.md)
- [Seasons & Epochs](../protocol/seasons-and-epochs.md)

## AIRTrading Engine diagram

![AIRTrading Engine Diagram](../assets/images/airtrading-engine-diagram.png)
