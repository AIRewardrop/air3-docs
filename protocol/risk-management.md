# Risk Management and Mass Exit Scenarios

This page explains what can happen to open positions if many users exit at the same time and how the protocol should mitigate risk.

## User-friendly premise (important)

AIR3 documentation should be clear without sounding alarmist.

Current intended operating posture described in this docs set:
- the vault is **not intended to run leveraged exposure**
- therefore the classic perp-style **liquidation risk from leverage should not apply** in the intended model

That said, real execution risk still exists and must be documented honestly.

## What happens if many users exit (example: 90%)

With the pro-rata withdrawal rule:
- the vault must reduce approximately 90% of **every** open position
- profits and losses are realized proportionally
- the remaining vault continues with the remaining position size (about 10% in this example)

This is a large forced portfolio reduction event.

In a no-leverage model, the main concern is typically **execution quality** (price impact, slippage, delay), not liquidation.

## What happens to mixed positions (some profit, some loss)

If the vault has multiple open positions and some are winning while others are losing:
- the protocol still closes the same percentage of **all** positions
- winning and losing legs are both reduced proportionally
- the user's realized exit value reflects the net result of their pro-rata share across the entire portfolio

This is the correct behavior for fair vault exits.

## Main risks during mass withdrawals (no leverage model)

### 1. Slippage and market impact
Large reductions can move the market against execution price:
- lower realized value for exits
- worse prices for remaining vault adjustments
- higher cost to unwind quickly

### 2. Execution lag
Closing many positions takes time (multiple orders / order updates).
During the unwind window, the market can move.

### 3. Fee drag and venue costs
Trading fees (and venue-specific costs where applicable) reduce net realized value, especially during high churn or stressed exits.

### 4. Venue / API constraints
API limits, order throttling, and exchange behavior can slow execution.

### 5. Strategy underperformance during volatility
Even without leverage, fast market moves can cause poorer exits and lower realized outcomes than idealized backtest prices.

## If leverage is ever enabled in a future version

If a future deployment enables leverage, then additional risks become material and must be reintroduced in docs and risk controls:
- margin pressure
- maintenance thresholds
- liquidation risk during unwind

Until then, docs should avoid presenting liquidation as a primary user risk for the intended no-leverage model.

## Protocol-level mitigation requirements (recommended)

### A. True pro-rata reduce-only exits
Never close selectively (only winners or only losers). Selective unwinds distort risk and can harm remaining users.

### B. Conservative sizing
Size positions so the vault can handle clustered user exits without chaotic unwinds.

### C. Controlled unwind mode
If withdrawal pressure exceeds a threshold:
- switch to controlled unwind / tranche execution
- preserve immediate exclusion from PnL for exiting users
- finalize exit value only from actual realized unwind output

### D. Stable cash buffer
Maintain a stable reserve when possible so smaller withdrawals do not require forced immediate unwinds.

### E. Risk-aware strategy sizing
Strategy sizing should account for the possibility of correlated user exits and stress conditions.

## Documentation rule

Users should be informed that:
- withdrawals stop exposure immediately (accounting)
- payout comes after delay
- final value depends on realized execution results
- stressed market conditions can affect realized exit value through slippage and fees

This is accurate, transparent, and user-friendly without overstating risks.
