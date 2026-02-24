# Supply, Burns, and Reporting

This page explains how AIR3 supply and burn information should be read and verified using public on-chain and market data sources.

## Supply Baseline

- **Launch model:** Fair launch on Moonshot (now moon.it), on Solana
- **Initial launch supply:** `1,000,000,000 AIR3`
- **Token mint (CA):** `2jvsWRkT17ofmv9pkW7ofqAFWSCNyJYdykJ7kPKbmoon`

## How to Read AIR3 Supply Today

AIR3 launched with a 1B token supply. Current circulating supply may be lower than the initial supply due to token burns.

For live values, users should verify supply and market data through public sources:
- [GeckoTerminal AIR3 pool page](https://www.geckoterminal.com/it/solana/pools/52utUc1BdCp8iYtNfHTj2UUBrAWEkrDuVVR2vGgcoRJE)
- [DexScreener AIR3 pair](https://dexscreener.com/solana/52utUc1BdCp8iYtNfHTj2UUBrAWEkrDuVVR2vGgcoRJE)
- [Solscan token account / mint view](https://solscan.io/account/2jvsWRkT17ofmv9pkW7ofqAFWSCNyJYdykJ7kPKbmoon)

## Burn Tracking

AIR3 burns reduce the effective circulating supply over time.

The recommended public verification approach is:
1. Start from the initial launch supply (`1,000,000,000 AIR3`)
2. Verify current circulating supply using market/explorer dashboards
3. Compare the delta to estimate cumulative burn impact
4. Cross-check major burn events and wallet flows on-chain where relevant

Because market dashboards and explorers update continuously, the values visible to users can change over time.

## Dev Wallet Disclosure

The AIR3 team discloses the dev wallet address for transparency.

- **Dev wallet:** `Ehvs2YznK9JNWHvMQ76i6Tj8wZQWKwgd8USmuWv478kz`

This disclosure helps users track wallet balances and flows directly on-chain. Wallet balances are informational and should be read together with the live circulating supply shown by public explorers and dashboards.

## Historical Mint / Early Buy Reference

The team also publishes the historical transaction reference associated with the mint-era buy disclosure.

- **Mint / early buy transaction (historical reference):** [Solscan transaction](https://solscan.io/tx/3GsBYHNTXQEKoHxPqoaF2t89SDsAUHu5YU7SrArGUzrN8vjAH26fL8isrF3EvhbaBEGkVD27GWwudj9pYj45BuTb)

This transaction is provided for transparency and historical context.

## Launch Infrastructure Context

AIR3 was launched through the Moonshot ecosystem (now moon.it), with Meteora liquidity infrastructure used in the launch path.

For general launchpad mechanics and liquidity model context:
- [moon.it docs](https://docs.moon.it/docs/welcome)
- [Meteora x Moonshot article](https://meteoraag.medium.com/meteora-x-moonshot-a-new-meta-for-memecoin-launchpads-9917b833a940)

## Related Pages

- [Tokenomics Overview](overview.md)
- [Market Structure and Liquidity](market-and-liquidity.md)
- [Contracts and Addresses](contracts-and-addresses.md)
