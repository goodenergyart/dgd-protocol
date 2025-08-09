# Architecture

## Components

- **Controller**: central orchestrator that coordinates interactions between vaults, oracle, fee management, and bridge.
- **BtcVault**: holds BTC collateral deposits; issues DGD tokens against BTC.
- **UsdcVault**: holds USDC liquidity to redeem DGD; manages liabilities and assets.
- **OracleRouter**: provides price feeds for BTC/USD and USDC; ensures up-to-date market data.
- **FeeManager**: calculates and collects fees on operations; maintains fee reserves.
- **BridgeAdapter**: interface to cross-chain bridge for moving BTC to/from the protocol.

## Invariants

- `dgdSupply <= btcValue / LTV`: total DGD issued must not exceed collateral value divided by the loan‑to‑value ratio.
- `usdcLiabilities <= usdcAssets + feeReserve`: USDC liabilities must be covered by assets plus fee reserves.
- The protocol can pause if a price feed is stale or health factor (HF) < 1.0.

## Parameters

- **Loan‑to‑Value (LTV)**: 50 % — DGD supply must not exceed 50 % of BTC collateral value.
- **Fee**: 1 % on DGD→USDC redemptions.
- **Repay Fee**: 0 %.
