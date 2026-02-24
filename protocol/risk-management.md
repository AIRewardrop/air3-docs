# Risk Management and Operational Limits

This page describes the main user-facing risks and operational edge cases relevant to the AIRTrading Engine, together with the mitigation approach described in this documentation set.

The intended operating model documented here is **no leverage**. Risk communication therefore focuses on execution and market risks rather than leverage-driven liquidation scenarios.

## Risk categories

### 1) Adverse market moves

**What it is**  
Market prices can move against a strategy after entry or during an unwind.

**Why it matters**  
This affects realized outcomes, user exit values, and epoch performance.

**Mitigation approach**  
- strategy validation on AIRTrack before deployment
- rule-based stop logic and target management
- controlled execution procedures
- portfolio-level monitoring and strategy review

### 2) Slippage

**What it is**  
The executed price may differ from the expected price, especially during volatility or lower liquidity conditions.

**Why it matters**  
Slippage can reduce realized PnL, reduce exit values, and affect fairness during high-volume withdrawal events.

**Mitigation approach**  
- staged order execution where appropriate
- liquidity-aware execution logic
- conservative assumptions in performance review
- transparent reporting of realized outcomes rather than estimated outcomes

### 3) Execution timing

**What it is**  
The protocol and execution stack may require time to process pro-rata reductions, settlement actions, and periodic accounting.

**Why it matters**  
Timing differences can affect realized prices and can increase operational variance during stressed markets.

**Mitigation approach**  
- deterministic accounting rules (pro-rata closes, ExitTicket creation, epoch settlement rules)
- immediate user exclusion from PnL after WithdrawRequest to prevent double allocation
- operational procedures for orderly execution and reconciliation

### 4) Fees and venue costs

**What it is**  
Trading fees, swap costs, and other venue-related execution costs reduce net outcomes.

**Why it matters**  
Gross performance and net distributable performance are not the same.

**Mitigation approach**  
- explicit fee treatment in settlement logic
- net-profit accounting before AIR3 split
- user-facing documentation of fee impact in examples and formulas

### 5) Strategy underperformance

**What it is**  
A validated strategy can still underperform after deployment because market conditions change.

**Why it matters**  
Historical or simulated performance does not guarantee future performance.

**Mitigation approach**  
- AIRTrack live validation before promotion
- ongoing review and performance monitoring
- strategy deactivation / replacement procedures (implementation-specific)
- transparent communication of results

### 6) Temporary delays under stress conditions

**What it is**  
Periods of unusual market activity or simultaneous user actions may increase execution and reconciliation time.

**Why it matters**  
Users may experience slower processing of operational steps even when accounting rules remain unchanged.

**Mitigation approach**  
- fixed and deterministic withdrawal settlement model (ExitTicket + 7-day delay)
- orderly processing for pro-rata closes
- clear event logging and status communication

## Mass exit scenario (many users request withdrawal)

If many users request withdrawal in a short window, the protocol applies the same core rule consistently:

- each user exit is processed using their percentage share at request time
- the vault closes the same percentage of all open positions pro-rata
- exit balances are created as ExitTickets
- users are excluded immediately from further PnL and epoch rewards

### Practical effect on positions

A large aggregate withdrawal ratio (for example, 90% of total vault value) reduces approximately the same percentage of each open position. The vault portfolio is resized rather than selectively closed.

This is operationally intensive and may increase slippage and execution variance, but the accounting rule remains consistent.

## Operational limits and implementation-specific controls

The following controls are implementation-specific and may vary by deployment version:

- order execution throttling / staging
- venue-side execution parameters
- stable buffer targets
- strategy-level size limits
- temporary operational safeguards during abnormal conditions

## Related pages

- [Withdraw Flow (7-Day Delay)](withdraw-flow.md)
- [Seasons and Epochs](seasons-and-epochs.md)
- [Pacifica Execution Layer](pacifica-execution-layer.md)
- [Risks, Limits, and Disclaimers](../security/risks-limits-and-disclaimers.md)
