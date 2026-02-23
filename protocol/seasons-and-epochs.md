# Seasons and Epochs

The AIRTrading design adds a season/epoch accounting layer on top of the vault withdrawal model.

## Why epochs exist

Epochs make profit accounting deterministic and auditable by creating periodic settlement windows.

At epoch end, the system can:
- realize PnL in stable (Option A model)
- apply protocol fee
- split net profit between buyback and users
- update rewards accounting for active users

## Definitions

- **Season**: a larger logical period containing multiple epochs
- **Epoch**: a configurable settlement window (days or week, depending on volume and operational needs)

## Option A settlement model (realized PnL in stable)

At the end of each epoch, the vault realizes PnL in stable by closing or reducing positions as needed.

This creates a distributable, deterministic result.

### Epoch PnL calculation (conceptual)
- `equityStart` = vault value at epoch start
- `equityEnd` = vault value at epoch end after settlement
- `epochPnL = equityEnd - equityStart`

## Settlement rules

### If epochPnL <= 0
- epoch is settled
- no profit distribution
- losses remain reflected in vault accounting

### If epochPnL > 0
1. apply protocol fee
2. compute net profit
3. split net profit:
   - 50% buyback
   - 50% users
4. convert profit legs according to protocol rules (stable -> AIR3 where applicable)
5. send buyback allocation and users allocation to the appropriate contracts/pools

## Compatibility with manual withdrawals

This model is designed to be compatible with manual withdrawals with 7-day delay.

Critical rule:
- if a user submits `WithdrawRequest` during an epoch and is excluded immediately, they do **not** participate in the current epoch distribution

That user has already crystallized their exit value via pro-rata close.

## Anti double-payment rule (must stay explicit)

The exclusion takes effect in the **current epoch**, not the next one.

Otherwise the user could be paid twice:
- once through pro-rata exit crystallization
- again through epoch reward allocation

## Operational notes

Epoch duration can be configured based on:
- volume
- strategy cadence
- execution venue constraints
- desired user experience for reward frequency
