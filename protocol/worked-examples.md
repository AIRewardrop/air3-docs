# Worked Examples

## Example 1: User exit at 30% vault share

Assume:
- vault total value now = 1,000
- user share value now = 300
- user weight now = 30%

Open positions:
- Position A
- Position B
- Position C

### Withdraw request behavior
The vault must close:
- 30% of A
- 30% of B
- 30% of C

The stable value recovered from these reductions becomes the user's exit allocation.

Then:
- create ExitTicket
- unlock in 7 days
- exclude user immediately from PnL and rewards (current epoch included)

## Example 2: Positive PnL on exit

Assume:
- user principal basis = 100 USDC
- pro-rata close realizes 120 USDC
- realized PnL = +20 USDC

Protocol outcome (example logic):
- principal/base return = 100 USDC stable
- profit component = 20 USDC
- convert profit to AIR3
- split AIR3:
  - 50% buyback
  - 50% user rewards

User receives:
- stable capital return
- AIR3 equivalent for the users half of profit

## Example 3: Negative PnL on exit

Assume:
- user principal basis = 100 USDC
- pro-rata close realizes 85 USDC
- realized PnL = -15 USDC

Outcome:
- payout stable = 85 USDC (after 7-day delay)
- AIR3 = 0
- loss is absorbed by the user's allocation

## Example 4: User withdraws during epoch (anti double-pay)

If a user sends `WithdrawRequest` during an epoch:
- the vault closes the user's pro-rata share immediately
- an ExitTicket is created
- user becomes excluded immediately
- user does not receive current epoch rewards

This prevents:
- one payout via exit crystallization
- a second payout via epoch distribution

## Example 5: Mass exit (90% of users by value)

If users representing 90% of vault value request exit:
- approximately 90% of every position is reduced
- remaining vault continues at ~10% position size
- risk depends on leverage, margin buffer, market movement, and execution quality
- protocol should enter controlled unwind mode if thresholds are hit
