# HydraDEX V3 API

## Overview

HydraDEX V3 is the primary decentralized exchange on Hydra Chain, using a Uniswap V3–compatible concentrated-liquidity AMM.  This page documents the **market data** and **GraphQL subgraph** endpoints for HydraDEX

It’s meant for integrators (aggregators, analytics sites, wallets, bots, etc.) who want to:

* Discover HydraDEX markets and basic stats
* Pull historical trades and volumes
* Query detailed on-chain data via the V3 subgraph
* Cross-check everything on the official Hydra explorer

This page describes:

* REST-style **market data APIs** (tickers and trade history)
* The **V3 subgraph** for deep on-chain analytics
* **Core contract addresses** for developers who want to integrate directly at the smart contract level

### Quick Reference

Base URLs:

* Hydra DEX V3 Subgraph (GraphQL)\
  <https://subgraph.hydrachain.org/subgraphs/name/v3-subgraph-temp/graphql>
* Market Data API – Tickers\
  <https://info.hydradex.org/api/tickers>
* Market Data API – Historical Trades\
  <https://info.hydradex.org/api/historical_trades>
* Hydra Chain RPC (HydraGon mainnet)\
  <https://rpc-mainnet.hydrachain.org/>
* Hydra Mainnet Explorer (Skynet)\
  <https://skynet.hydrachain.org/>
* HydraDEX Frontend\
  [https://hydradex.org](https://hydradex.org/)

***

### Network & Core Contracts

#### Hydra Chain – HydraGon Mainnet

* Network: Hydra Chain (HydraGon)
* Chain ID: 4488
* Native token: HYDRA
* RPC endpoint: <https://rpc-mainnet.hydrachain.org>
* Explorer: <https://skynet.hydrachain.org/>

#### Hydra DEX V3 Core Contracts (Hydra Mainnet)

All contract addresses below are on **HydraGon mainnet**.

* V3 Core Factory\
  0x664bC90358785F6C02c7e26696FE7E908CebAB86
* Multicall\
  0x42320aDeF5D9B5890292251f35A89B39EA42d61c
* TickLens\
  0x6C1EDf5bDEcaa1e87627c4Bacf58CB954c6A1869
* Swap Router\
  0x9740a64B7F448E4fcE0Db5c3f0F0a0Ae1796e643
* Nonfungible Position Manager (LP NFTs)\
  0x2Ff62B6EA2d6ED7bbcE8cc51b8D7402AeB671335
* Quoter\
  0x2f47EDDca7Ec038E542541E74FA8CA9558718773
* Wrapped HYDRA (WHYDRA)\
  0x900e563a74be93807e8a4a3b52d72a351badd6bf

Developers can use these addresses with Uniswap V3–compatible SDKs and tooling to:

* Route swaps
* Create pools
* Manage LP positions as NFTs
* Simulate quotes off-chain

***

### Market Data REST API

The REST endpoints on `info.hydradex.org` provide a simple way to:

* List markets
* Get last price and 24h stats
* Fetch raw trade history per pair

They are read-only, public, and do not require authentication.

Base path:

* <https://info.hydradex.org/api>

#### /tickers

**Endpoint**

* Method: GET
* URL: `/api/tickers`

Returns summary data for all active pairs listed on HydraDEX.

**Example request**

GET <https://info.hydradex.org/api/tickers>

**Example response (truncated)**

```jsonl
[
  {
    "ticker_id": "0x71f16bcb805566f322a0904885d6147a76c249c5_0x900e563a74be93807e8a4a3b52d72a351badd6bf",
    "base_currency": "0x71f16bcb805566f322a0904885d6147a76c249c5",
    "target_currency": "0x900e563a74be93807e8a4a3b52d72a351badd6bf",
    "pool_id": "0x97a59b3751bdba640c4f3d8c7af4547a7f31af3c",
    "last_price": "14.08544352542674692634239276296717",
    "liquidity_in_usd": "46047.77943597822317908055006865207",
    "base_volume": "11.088884091382596",
    "target_volume": "156.5759623589776",
    "bid": "14.08544352542674692634239276296717",
    "ask": "14.08544352542674692634239276296717",
    "high": "14.127686076532944",
    "low": "14.042777848935478"
  },
...
]
```

**Field reference**

* ticker\_id\
  Identifier for the trading pair. Format:\
  `{base_token_address}_{quote_token_address}`
* base\_currency\
  EVM address of the base token.
* target\_currency\
  EVM address of the quote token.
* pool\_id\
  Uniswap V3 pool contract address for this base/quote/fee tier.
* last\_price\
  Last traded price, expressed as quote token per base token.
* liquidity\_in\_usd\
  Approximate USD liquidity for the pool.
* base\_volume\
  24h volume of the base token (in units of base token).
* target\_volume\
  24h volume of the quote token (in units of quote token).
* bid / ask\
  Best bid and ask derived from the current pool state.
* high / low\
  High and low price over the last 24h window.

This endpoint is suitable for:

* Market list pages
* 24h volume rankings
* Ticker widgets and “where to trade” integrations

#### `/historical_trades`

**Endpoint**

* Method: GET
* URL: `/api/historical_trades`
* Required query parameter:
  * `ticker_id` – same format as in `/api/tickers`

Example:

GET <https://info.hydradex.org/api/historical_trades?ticker_id=0x900e563a74be93807e8a4a3b52d72a351badd6bf_0xbbf6f2d2d462185df545c744974b7eb6ddadfcfd>

This endpoint returns historical trade data for a specific market, typically including for each trade:

* trade identifier
* price
* base and quote volumes
* timestamp
* side (buy / sell or taker direction)

Exact field names and optional query parameters (for pagination or time filtering) should be inferred from the live response. Aggregators / Developers can use this endpoint to reconstruct:

* Candles / OHLCV
* Volume over arbitrary timeframes
* Recent trades streams

***

### Hydra DEX V3 Subgraph (GraphQL)

For deeper analytics and on-chain level data, HydraDEX exposes a Uniswap V3–style subgraph.

**Endpoint**

<https://subgraph.hydrachain.org/subgraphs/name/v3-subgraph-temp/graphql>

This is a standard GraphQL endpoint, compatible with GraphiQL, Apollo, urql, etc.

#### Authentication and rate limits

* No authentication required for public read access.
* Please use reasonable pagination (`first` / `skip`) and avoid extremely wide queries.
* Caching results is recommended for production integrations.

If formal public rate limits are introduced, they can be documented on this page later.

#### Core entity types (conceptual)

The schema follows a typical Uniswap V3–style design. While field names may vary slightly, you can expect:

* Token
  * ERC-20–style metadata (address, symbol, name, decimals)
  * Derived prices and liquidity metrics
* Pool
  * token0 / token1 addresses
  * fee tier
  * liquidity
  * sqrtPrice, current tick, TVL and volume metrics
* Tick
  * Liquidity at particular tick indices for each pool
* Position
  * LP NFT positions
  * owner, pool, liquidity
  * lower and upper ticks
  * deposited tokens, uncollected fees
* Swap
  * Individual swaps (amount0, amount1, amountUSD)
  * sender, recipient, timestamp, transaction reference
* Mint / Burn / Collect
  * Liquidity add/remove events
  * Fee collection events
* PoolDayData, PoolHourData
  * Aggregated stats by pool and time window
* TokenDayData
  * Daily volume and liquidity per token
* Factory / Bundle
  * Global stats (total volume, total TVL, reference HYDRA price)

You can introspect the exact schema from the endpoint using any GraphQL tooling that supports `__schema` introspection.

#### Example GraphQL queries

Below are example queries you can use as templates. Adjust field names if your introspection shows slight differences.

1. **Top pools by TVL**

```graphql
query TopPools($first: Int = 10) {
pools(
first: $first
orderBy: totalValueLockedUSD
orderDirection: desc
) {
id
token0 { id symbol name }
token1 { id symbol name }
feeTier
totalValueLockedUSD
volumeUSD
}
}
```

Use this for:

* “Top pools” lists
* TVL rankings
* Basic market dashboards

2. **Pool details by address**

```graphql
query PoolByAddress($poolAddress: ID!) {
pool(id: $poolAddress) {
id
token0 { id symbol decimals }
token1 { id symbol decimals }
feeTier
liquidity
sqrtPrice
tick
totalValueLockedToken0
totalValueLockedToken1
totalValueLockedUSD
}
}
```

Use this for:

* Reconstructing on-chain spot prices
* Fetching current reserves and TVL
* Showing pool parameters and fee tier

3. **LP positions for a wallet**

```graphql
query PositionsByOwner($owner: String!) {
positions(where: { owner: $owner }) {
id
pool {
id
token0 { symbol }
token1 { symbol }
feeTier
}
liquidity
tickLower { tickIdx }
tickUpper { tickIdx }
depositedToken0
depositedToken1
collectedFeesToken0
collectedFeesToken1
}
}
```

Use this for:

* LP dashboards
* Showing user positions and ranges
* Tracking collected fees

4. **Swaps for a pool since a given time**

```graphql
query SwapsForPool(
$poolAddress: String!
$fromTimestamp: Int!
) {
swaps(
where: {
pool: $poolAddress
timestamp_gte: $fromTimestamp
}
orderBy: timestamp
orderDirection: asc
) {
id
timestamp
sender
recipient
amount0
amount1
amountUSD
}
}
```

Use this for:

* Trade history
* Volume calculations
* Arbitrage and flow analysis

#### Mapping REST data to subgraph data

A typical workflow for integrators:

1. Call `/api/tickers` to discover all active markets.
2. For each market:
   * Read `ticker_id` and split into `base/quote` token addresses.
   * Read `pool_id` as the pool contract address.
3. Use `pool_id` as `pool(id: ...)` in the subgraph to:
   * Fetch pool configuration (fee tier, tokens, TVL).
   * Fetch `swaps`, `mints`, `burns`, and pool day/hour data.
4. Optionally use `/api/historical_trades` to cross-check the same volume/trade data in a simple REST format.

***

### Explorer Cross-Checks

All liquidity and trades on HydraDEX V3 are on-chain. To verify any data:

1. Take a `pool_id` or token address from `/api/tickers`.
2. Open it on the Hydra explorer:\
   <https://skynet.hydrachain.org/>
3. Inspect:
   * Token contracts
   * Pool contracts
   * Individual swap transactions
   * Liquidity add/remove events

This makes it straightforward to reconcile:

* REST data
* Subgraph data
* Raw EVM on-chain events

***

### Notes for Integrators

* HydraDEX is a **non-custodial Uniswap V3–style DEX**. There are no user accounts, no CEX-like order books, and no fiat deposits/withdrawals.
* The combination of:

  * `/api/tickers`
  * `/api/historical_trades`
  * The V3 subgraph
  * Skynet explorer

  is generally sufficient for:

  * Exchange listings
  * Price tracking and OHLCV charts
  * TVL and liquidity analytics
  * LP and pool dashboards
* If you need additional helper endpoints (for example, pre-aggregated candles), they can usually be derived from the existing subgraph and trade history data. You can reach out to the Hydra team for coordination if required.

For questions, integrations, and technical support:

* X (Twitter):\
  <https://x.com/hydrachainorg>
* Telegram – Global community:\
  <https://t.me/hydrachain>

You can also open issues or pull requests in the Hydra Chain GitHub organization for technical feedback and improvements.
