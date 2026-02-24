# FAQ

## What is AIRewardrop?
AIRewardrop is the ecosystem/company building autonomous AI agent infrastructure for crypto, including AIR3 and related dApp modules.

## What is AIR3?
AIR3 is the flagship AI agent and MetaHuman interface of the ecosystem, with analytics, live interaction, and tokenized product utility layers.

## Is AIRTrack the autotrading product?
No.

AIRTrack is a **tracking and simulation** layer used to test strategies live and record performance transparently.

## What is AIRTrading then?
AIRTrading is the **execution layer**. It is the vault-based protocol/execution product for strategies that passed live testing on AIRTrack.

## Why split AIRTrack and AIRTrading?
To keep strategy testing transparent and separate from real execution risk. AIRTrack validates behavior. AIRTrading executes only proven strategies.

## How are trades made transparent to users?
AIR3 uses multiple transparency layers:
- AIRTrack / AIRdApp trade history and PnL tracking
- on-chain/protocol accounting events (for vault/withdraw/settlement flows)
- X posts on https://x.com/AIRewardrop when trades open and close (including close confirmation cards with PnL)

## How do withdrawals work in AIRTrading?
Conceptually:
- user share is frozen at request time
- the same percentage of all positions is closed
- an ExitTicket is created
- user is excluded from PnL immediately
- claim happens after a fixed 7-day delay

## What happens if the user exits with a loss?
Loss is absorbed by the user's allocation. The user receives reduced stable payout and no AIR3 profit reward.

## What happens if many users exit at once?
The vault must reduce the same percentage of all positions (pro-rata). The main user-facing risks in the intended no-leverage model are slippage, execution delay, and fees during large unwinds.

## Is liquidation risk a core AIRTrading user risk?
Not in the intended no-leverage operating model documented here.

If leverage is introduced in future versions, margin and liquidation risk must be documented explicitly.

## What is AIRSponsor?
A buy + burn utility flow that unlocks sponsor slots in AIR3 live content, including on-screen presence and scripted call-outs.

## What is AIRTool?
A buy + burn utility flow that unlocks AIR3 agent deployment/rental for third-party Telegram and/or Discord communities.

## Is this financial advice?
No. AIR3 documentation is informational and product-focused. Users should do their own due diligence.
