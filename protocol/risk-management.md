# Risk Management and Mass Exit Scenarios

This page explains what can happen to open positions if many users exit at the same time and how the protocol should mitigate risk.

## What happens if many users exit (example: 90%)

With the pro-rata withdrawal rule:
- the vault must reduce approximately 90% of **every** open position
- profits and losses are realized proportionally
- the remaining vault continues with the remaining position size (about 10% in this example)

This is a large deleveraging event.

It is not automatically a liquidation event by itself, but it can become dangerous depending on leverage, margin buffer, market volatility, and execution quality.

## What happens to mixed positions (some profit, some loss)

If the vault has multiple open positions and some are winning while others are losing:
- the protocol still closes the same percentage of **all** positions
- winning and losing legs are both reduced proportionally
- the user's realized exit value reflects the net result of their pro-rata share across the entire portfolio

This is the correct behavior for fair vault exits.

## Main risks during mass withdrawals

### 1. Slippage and market impact
Large reductions can move the market against execution price:
- lower realized value for exits
- worse prices for remaining vault adjustments
- higher cost to unwind quickly

### 2. Execution lag
Closing many positions takes time (multiple orders / order updates).
During the unwind window, the market can move against the vault.

### 3. Margin pressure and liquidation risk
If the vault runs high leverage or thin margin buffer:
- adverse price movement during unwind can push equity toward maintenance margin
- liquidation risk increases before the unwind completes

### 4. Venue constraints
API limits, order throttling, and exchange behavior can slow execution.

### 5. Funding and fees
Funding and trading fees continue to affect equity and can worsen outcomes in stressed conditions.

## Protocol-level mitigation requirements (recommended)

### A. True pro-rata reduce-only exits
Never close selectively (only winners or only losers). Selective unwinds distort risk and can harm remaining users.

### B. Vault leverage cap
Keep leverage under a defined vault-level maximum.

### C. Margin buffer target
Enforce a minimum margin safety buffer before allowing full strategy sizing.

### D. Controlled unwind mode
If withdrawal pressure exceeds a threshold:
- switch to controlled unwind / tranche execution
- preserve immediate exclusion from PnL for exiting users
- finalize exit value only from actual realized unwind output

### E. Stable cash buffer
Maintain a stable reserve when possible so smaller withdrawals do not require forced immediate unwinds.

### F. Risk-aware strategy sizing
Strategy sizing should account for the possibility of correlated user exits and stress conditions.

## Documentation rule

Users should be informed that:
- withdrawals stop exposure immediately (accounting)
- payout comes after delay
- final value depends on realized execution results
- stressed market conditions can affect realized exit value through slippage and fees
