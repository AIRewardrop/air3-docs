# Withdraw Flow (7-Day Delay)

This page documents the AIRTrading withdrawal sequence for users exiting a shared vault allocation.

## Overview

AIRTrading uses a single-vault model. Each user owns a share of the vault based on the current value of their allocation relative to total vault equity.

When a user requests withdrawal, the protocol settles that user by closing the same percentage of **all** open positions, recording the realized result, and releasing funds after a fixed 7-day delay.

## Core withdrawal logic

When a user submits a withdrawal request:

1. The protocol locks the user share percentage at request time (`exitPctNow`)
2. The vault reduces **all** open positions pro-rata using the same percentage
3. The realized proceeds are recorded as the user's exit allocation
4. An `ExitTicket` is created with a fixed unlock time (`now + 7 days`)
5. The user is excluded immediately from subsequent vault PnL and epoch distributions (including the current epoch)

During the 7-day delay, the user is no longer exposed to vault PnL because the user allocation has already been reduced out of the vault and recorded in the exit flow.

## Step-by-step sequence

### 1) Determine the user exit share

The protocol computes the user's current vault weight at the moment of the request.

- `exitPctNow = userWeightNow`

Example:
- `vaultTotalEquityNow = 1,000`
- `userShareValueNow = 300`
- `exitPctNow = 30%`

### 2) Reduce all open positions pro-rata

If the vault holds positions A, B, and C, and `exitPctNow = 30%`, the protocol reduces:

- 30% of position A
- 30% of position B
- 30% of position C

This preserves fairness across users because the exiting user receives the realized result of the same proportional exposure they held in the vault.

### 3) Record the realized exit allocation

The stable value recovered from the pro-rata reductions becomes the user's exit allocation.

Recommended terminology:

- `realizedValueForUser`: stable value realized from the pro-rata close
- `principalBasisForUser`: accounting basis used to measure user PnL
- `realizedPnlForUser = realizedValueForUser - principalBasisForUser`

This naming keeps a clear distinction between:
- **vault share** (percentage)
- **principal basis** (accounting reference)
- **realized value** (actual proceeds from the withdrawal unwind)

### 4) Create ExitTicket (fixed delay)

An `ExitTicket` is created with the data required for settlement and claim.

Minimum fields:
- `exitValueStable`
- `pnlUser` (positive or negative)
- `unlockTime = now + 7 days`

### 5) Apply immediate exclusion (anti double-counting)

From the moment the withdrawal request is accepted:

- `userExcluded = true`
- the user is not exposed to further vault PnL
- the user does not participate in epoch reward calculations
- current epoch inclusion is removed immediately (no carryover to next epoch)

This prevents overlap between:
- withdrawal settlement, and
- epoch-based profit distribution

## Recommended auditable event structure

`WithdrawRequested(user)`

Suggested fields:
- `vault_equity_now`
- `user_weight_now`
- `close_ratio`
- `positions_closed_summary`
- `realized_value_stable`
- `principal_basis_user`
- `realized_pnl`
- `unlock_time`

## User-facing communication (clear wording)

Recommended UI messaging:

- "Withdrawal request accepted. We are reducing your current share across all vault positions."
- "Your vault share has been removed from active exposure."
- "Your exit value and realized PnL have been recorded."
- "Funds will be claimable in 7 days."

## Positive and negative settlement outcomes

### If realized PnL is positive

If `pnlUser > 0`:
- the profit component may be converted into AIR3 (implementation-specific rules apply)
- profit distribution follows the protocol split logic (including fee treatment where applicable)
- the capital component remains denominated in stable
- the user receives the user allocation of the profit split in AIR3

### If realized PnL is negative

If `pnlUser < 0`:
- the loss is absorbed by the user's allocation
- the stable payout is reduced accordingly
- no AIR3 reward is distributed from a loss

## Why this model is used

This withdrawal model improves accounting clarity and fairness by separating:

- **withdrawal settlement** (user-specific realized result at request time)
- **epoch distributions** (active-user profit sharing only)

It also gives the user a deterministic path:
request -> pro-rata reduction -> ExitTicket -> delayed claim.
