# Docs Migration Notes

This package is a Docs v2 content refresh intended to replace or progressively overwrite legacy GitBook content.

## What this pack updates

- Introduces a modern product structure around AIR3, AIRTrack, AIRTrading, AIRSocial, AIRSponsor, and AIRTool
- Adds explicit AIRTrack vs AIRTrading separation
- Adds AIRTrading vault protocol documentation:
  - pro-rata withdrawals
  - 7-day delayed payout
  - current-epoch exclusion (anti double-pay)
  - season/epoch settlement logic
  - rewards/buyback split
  - risk and mass exit scenarios
  - Pacifica execution layer notes
- Adds screenshot-based product pages for AIRdApp modules
- Adds updated roadmap framing and FAQ

## Recommended import workflow

1. Create a branch (example: `docs-v2-refresh`)
2. Copy this pack into the root of `air3-docs` (overwrite existing files if intended)
3. Commit and push
4. Review GitBook rendering and sidebar
5. Iterate on wording, tokenomics details, and campaign parameters

## Important editorial rule kept in this pack

AIRTrack is documented as tracking/simulation only.
AIRTrading is documented as execution only for strategies validated on AIRTrack.
