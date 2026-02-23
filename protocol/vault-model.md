# Vault Model

## Single portfolio model

The vault is a single portfolio with open positions. Each user "weighs" a percentage of the vault based on the current value of their share compared to total vault value.

This means:
- users do not map 1:1 to specific positions
- users own a percentage claim on the vault
- exits must be handled pro-rata across the full position set

## User share mechanics (conceptual)

At any point in time:
- `vaultTotalValueNow` = current total value of the vault
- `userShareValueNow` = current value attributed to the user
- `userWeightNow` = `userShareValueNow / vaultTotalValueNow`

This `userWeightNow` is the basis for exit percentage calculation when a withdrawal is requested.

## Why pro-rata is required

If a user owns 30% of the vault and the vault holds positions A, B, C:
- the user cannot be assigned only the winning positions or only the losing positions
- the vault must close **30% of A, 30% of B, and 30% of C**

This keeps accounting fair and auditable.

## Auditability requirement

The smart contract system should emit enough data for third-party verification:
- vault value at request time
- user weight at request time
- close ratio used
- amount/value realized from position reductions
- payout basis and PnL sign
- unlock time for final claim

## Positive and negative PnL symmetry

The model must treat both sides symmetrically:
- positive PnL increases the user exit value
- negative PnL reduces the user exit value

No hidden smoothing should be assumed unless explicitly implemented and documented (e.g., reserve buffers).
