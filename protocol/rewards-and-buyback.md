# Rewards and Buyback

This page defines the profit split behavior used by AIRTrading after profit realization.

## High-level flow

When profit is realized (epoch settlement and/or eligible withdrawal profit logic):
1. apply protocol fee (if applicable to that path)
2. compute net profit
3. convert profit component to AIR3 (per protocol rule)
4. split net AIR3 allocation:
   - 50% buyback treasury
   - 50% users rewards

## Split rule

Net profit split:
- **50% Buyback**
- **50% Users**

This split should be documented as a protocol parameter if governance may update it in the future.

## User reward delivery model (recommended scalable approach)

To avoid iterating over all users on-chain, use an index-based claim model.

### Concepts
- `activeWeight` = total participating weight (excluding users who requested withdrawal)
- `rewardIndex` = cumulative reward per unit weight
- `userIndexLast` = last claimed index per user

### On epoch settlement
- `rewardIndex += usersPartAIR3 / activeWeight`

### On user claim
- `claimableAIR3 = userWeight * (rewardIndex - userIndexLast)`
- update `userIndexLast = rewardIndex`

This supports scale and keeps on-chain cost manageable.

## Withdrawal-specific positive PnL (if enabled)

For a withdrawal with positive realized PnL:
- capital/base amount can be returned in stable
- profit component can be converted to AIR3
- AIR3 split applies 50/50 buyback/users
- user receives only the users half of the profit component

This must be implemented consistently with epoch accounting to avoid duplication.

## Treasury roles (conceptual)

- **Buyback Treasury**: receives buyback-side AIR3 allocation
- **Rewards Pool**: receives user-side AIR3 allocation for claim

## Auditability requirements

Recommended emitted data on settlement:
- gross profit
- fee
- net profit
- buyback allocation
- users allocation
- conversion output (if swap performed)
- activeWeight used
- rewardIndex after update
