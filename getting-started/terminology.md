# Terminology

## Core ecosystem terms

**AIRewardrop**  
Company / ecosystem brand building autonomous agent infrastructure for crypto.

**AIR3**  
Flagship agent and ecosystem utility token hub on Solana. Also the public-facing MetaHuman live analyst.

**AIRdApp**  
The main product portal/UI where AIR modules are exposed (AIRTrack, AIRTrading, AIRSocial, AIRSponsor, AIRTool).

## Product terms

**AIRTrack**  
Tracking and simulation layer. Used to test strategies live and record performance. No user-fund execution.

**AIRTrading**  
Execution layer for strategies that pass AIRTrack live testing. Handles vault execution, withdrawals, epoch settlement, and rewards logic.

**AIRSocial**  
Community points / missions / leaderboard layer.

**AIRSponsor**  
Buy + burn access flow to obtain sponsored visibility inside AIR3 live streams/overlays and scripted call-outs.

**AIRTool**  
Token-gated AIR3 agent rental for third-party Telegram/Discord communities.

## Vault/protocol terms

**Vault**  
Single portfolio with open positions. Users own a percentage of total vault value, not isolated per-position wallets.

**User Weight Now**  
User share of total vault value at a specific moment.

**ExitPctNow**  
The user withdrawal percentage frozen at withdraw request time. This same percentage is closed on all open positions.

**ExitTicket**  
On-chain accounting record for a user withdrawal, claimable after the fixed delay.

**Excluded**  
Flag indicating the user is no longer exposed to vault PnL and no longer participates in epoch rewards from the withdrawal request onward (including the current epoch).

**Season / Epoch**  
Configurable accounting windows used to realize and distribute protocol PnL.
