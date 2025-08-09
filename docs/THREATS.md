# Threats and Mitigations

## Key Threats

- **Bridge failure**: loss or delay of BTC or USDC due to issues with the cross‑chain bridge.
- **Oracle failure**: stale or incorrect price data from the oracle leading to mispricing.
- **Re‑entrancy**: smart contract functions could be exploited to drain funds if re‑entrancy is not properly guarded.
- **Price shock**: sudden BTC price crash could leave collateral under‑secured.
- **Run on the USDC vault**: large redemptions could exhaust USDC liquidity before new BTC collateral arrives.

## Mitigations

- **Pauser**: emergency pause functionality to halt operations during anomalies.
- **Caps and rate limits**: limit the amount of BTC deposits and USDC redemptions per block or time window.
- **Redemption queue**: queue redemptions to smooth out liquidity demands and prevent bank‑run dynamics.
- **Robust Oracle**: use multiple price feeds with fallback and staleness checks.
- **Secure Bridge**: integrate with audited bridge contracts and monitor their health.
- **Defense against re‑entrancy**: use checks‑effects‑interactions pattern and re‑entrancy guards in contracts.
