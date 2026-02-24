# Worked Examples

These examples use consistent terminology:

- **vault weight / user share** = the user's percentage of current vault equity
- **principal basis** = accounting basis used to calculate realized PnL
- **realized value** = stable proceeds actually recovered from the pro-rata reduction of positions

## Example 1: User exits at 30% vault share

Assume:
- `vaultTotalEquityNow = 1,000`
- `userShareValueNow = 300`
- `userWeightNow = 30%`

Open positions:
- Position A
- Position B
- Position C

### Withdrawal behavior

The protocol reduces:
- 30% of position A
- 30% of position B
- 30% of position C

The stable proceeds from those reductions become the user's `realizedValueForUser`.

Then the protocol:
- creates an `ExitTicket`
- sets `unlockTime = now + 7 days`
- excludes the user immediately from vault PnL and epoch rewards (including the current epoch)

## Example 2: Positive realized PnL on withdrawal

Assume:
- `principalBasisForUser = 100 USDC`
- `realizedValueForUser = 120 USDC`

Calculation:
- `realizedPnlForUser = 120 - 100 = +20 USDC`

Illustrative settlement flow (protocol rules and fees may be implementation-specific):
- capital component in stable: `100 USDC`
- profit component: `20 USDC`
- profit component may be converted to AIR3
- AIR3 profit split:
  - 50% buyback allocation
  - 50% user allocation

User settlement:
- stable capital return
- AIR3 equivalent for the user portion of positive realized PnL

## Example 3: Negative realized PnL on withdrawal

Assume:
- `principalBasisForUser = 100 USDC`
- `realizedValueForUser = 85 USDC`

Calculation:
- `realizedPnlForUser = 85 - 100 = -15 USDC`

Settlement outcome:
- `payoutStable = 85 USDC` (claimable after the 7-day delay)
- `AIR3 reward = 0`
- the loss is absorbed by the user's allocation through the lower realized value

## Example 4: Withdrawal request during an active epoch (anti double-counting)

A user sends `WithdrawRequest` while an epoch is still active.

Protocol behavior:
- the vault reduces the user's pro-rata share immediately
- an `ExitTicket` is created
- the user is excluded immediately from active PnL participation
- the user is excluded from current-epoch reward allocation

Result:
- the user is settled through the withdrawal path only
- the user does not receive a second allocation via epoch settlement

## Example 5: Large concurrent exits (90% of vault equity requests withdrawal)

If users representing 90% of vault equity request withdrawal in a short window:

- the protocol attempts to reduce approximately 90% of each open position pro-rata
- the remaining active vault continues with a materially smaller position base
- realized values for exiting users depend on execution quality, market conditions, fees, and slippage during the unwind
- temporary processing or execution delays may occur under stressed conditions
- implementation-specific safeguards can trigger controlled unwind modes, batching, or temporary limits

This example highlights an operational stress case, not a change to the core accounting model.
