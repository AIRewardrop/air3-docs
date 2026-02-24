# AIRTrading FAQ

## What is AIRTrading?

AIRTrading is the real execution layer of the AIR3 ecosystem, where validated strategies can be deployed after passing live testing on AIRTrack.

## How does the Vault model work in simple terms?

AIRTrading uses a single Vault portfolio with open positions. Each user owns a quota, and each quota represents a percentage of the total Vault value.

## How does a withdrawal request work?

When a user submits a withdrawal request:
1. The protocol calculates the user share percentage at request time
2. The Vault closes the same pro-rata percentage of all open positions
3. The protocol creates an ExitTicket with the realized settlement values
4. Funds become claimable after a fixed 7-day delay

During the delay, the user is no longer exposed to ongoing Vault PnL because the user allocation has already been separated from active exposure.

## Is the user still included in rewards after requesting a withdrawal?

No. The user is excluded immediately from ongoing PnL exposure and Epoch reward distributions once the withdrawal request is accepted and the pro-rata close is executed.

## What happens if the user exits with negative PnL?

Losses are absorbed by the user allocation. In that case, the realized value is lower than the user principal basis and the payout reflects the realized value after losses.

## How are positive profits handled?

At protocol level, positive Epoch PnL can be settled in stable assets and split according to protocol rules (including AIR3 buyback and user allocation flows, after fees as applicable). User-specific settlement depends on implementation and product configuration.

## Does AIRTrading use leverage?

AIRTrading is presented with a no-leverage intended operating model. The primary user risks are adverse market moves, slippage, execution timing, fees, and strategy underperformance.
