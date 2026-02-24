# Risks, Limits, and Disclaimers

## General risk statement

AIR3 ecosystem products may involve:
- market risk
- execution risk
- platform/venue risk
- contract risk
- oracle/price-source effects (where relevant)
- fees and operational costs
- operational risk

Users can lose capital.

## Product-specific boundaries

### AIRTrack
AIRTrack is for tracking and simulation/testing. It is not the real execution vault and should not be described as user-fund autotrading.

### AIRTrading
AIRTrading is execution and therefore carries the highest risk profile in the stack.

For the intended no-leverage operating model described in these docs, the main user risks are:
- slippage
- execution lag under stress
- venue/API constraints
- strategy underperformance
- fees / execution costs

If leverage is introduced in future versions, the docs must explicitly add margin/liquidation risks back into the primary risk section.

### AIRSocial / AIRSponsor / AIRTool
These are utility/service modules and should still be governed by clear campaign and service terms.

## Mass withdrawal risk

Large simultaneous exits can force large pro-rata reductions across positions.
This can create:
- slippage
- adverse execution
- reduced realized exit values vs idealized mark values
- temporary operational stress during unwind

## No guarantee language

Documentation should avoid implying:
- guaranteed returns
- uniform profit percentages for all users
- risk-free automation
- always-positive epoch distributions

## Financial advice disclaimer

Nothing in the AIR3 docs should be interpreted as financial advice.
Users should perform their own due diligence and evaluate risk independently.
