# Withdraw Flow (7-Day Delay)

This page documents the core withdrawal behavior for AIRTrading.

## Core rule

When a user requests to exit:

1. Freeze their vault percentage **now**
2. Close the same percentage of **all** open positions
3. Create an exit balance (realized value)
4. Pay after a fixed **7-day delay**
5. Exclude the user from any further PnL immediately (including the current epoch)

The user is no longer exposed during the delay because their share has already been closed and segregated.

## Withdrawal sequence

### Step 1: Freeze user share
- `exitPctNow = userWeightNow`

Example:
- Vault total value now = 1,000
- User share value now = 300
- `exitPctNow = 30%`

### Step 2: Pro-rata close all open positions
If the vault has positions A, B, C and `exitPctNow = 30%`:
- close 30% of A
- close 30% of B
- close 30% of C

This action must be reduce-only at the strategy executor / venue side.

### Step 3: Create the exit balance
The stable value actually recovered from the pro-rata close is the user exit allocation.

- `realizedValueForUser = stable recovered from pro-rata close`
- `realizedPnlForUser = realizedValueForUser - userPrincipalBasis`

### Step 4: Create ExitTicket with fixed delay
An exit ticket is created with:
- `exitValueStable`
- `pnlUser` (positive or negative)
- `unlockTime = now + 7 days`

### Step 5: Immediate exclusion (anti double-pay)
From the withdraw request onward:
- `userExcluded = true`
- the user is not exposed to further PnL
- the user does not participate in epoch rewards (including current epoch)

This is explicitly **current epoch exclusion**, not next epoch exclusion.

## Auditable event (recommended shape)

`WithdrawRequested(user)`

Fields (example):
- `vault_equity_now`
- `user_weight_now`
- `close_ratio`
- `positions_closed_summary`
- `realized_value_stable`
- `user_principal_basis`
- `realized_pnl`
- `unlock_time`

## UI / user-facing messages (clear wording)

Recommended messages:
- "Withdrawal request accepted. We are closing X% of all vault positions (your current share)."
- "You are no longer exposed to vault PnL from this moment."
- "Funds will be claimable in 7 days."
- "Your exit value and PnL have been recorded in your ExitTicket."

## Positive PnL case on withdrawal

If `pnlUser > 0`:
- profit component can be converted into AIR3
- split 50% buyback / 50% user reward (after fee, if applied on exit profit)
- principal/base capital returns in stable
- user profit share is paid in AIR3 (users half)

## Negative PnL case on withdrawal

If `pnlUser < 0`:
- loss is absorbed by the user's allocation
- user receives lower stable payout
- no AIR3 reward is minted/distributed from a loss

## Why this model is robust

This model prevents double counting by separating:
- user exit value (crystallized now)
- epoch reward base (active users only)
