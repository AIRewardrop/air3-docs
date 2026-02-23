# AIRTrading Protocol Overview

AIRTrading Engine is a vault-based execution protocol design for strategies running on Pacifica perpetuals.

It is designed to be:
- auditable
- deterministic in user exits
- compatible with epoch-based profit accounting
- compatible with AIR3 buyback and user reward distribution

## Core principles

1. **Single vault portfolio**
   - The vault is one portfolio with open positions.
   - Users own a percentage of vault value, not isolated positions.

2. **Pro-rata exits**
   - On withdraw request, the vault closes the same percentage of every open position.
   - This prevents selective closing behavior.

3. **Immediate exclusion from PnL**
   - After withdraw request, the user is no longer exposed to PnL (positive or negative), starting immediately in the current epoch.

4. **Delayed payout**
   - Funds are paid after a fixed 7-day delay through an exit ticket claim flow.

5. **Epoch settlement**
   - PnL can be realized in stable at epoch end (Option A model) and distributed with a 50/50 split between buyback and users after fees.

## Scope of this section

This protocol section documents the operating logic and accounting model. It does not claim final deployed contract implementation details unless explicitly stated by the deployed version.

## Architecture reference

![AIRTrading Engine Diagram](../assets/images/airtrading-engine-diagram.png)
