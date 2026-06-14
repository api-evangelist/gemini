# Gemini Exchange GraphQL Schema

This document describes a conceptual GraphQL schema for the [Gemini Exchange](https://gemini.com) cryptocurrency exchange API. Gemini is a regulated cryptocurrency exchange offering REST and WebSocket APIs for trading, market data, account management, clearing, and institutional services.

**Note:** This is the Gemini cryptocurrency exchange (gemini.com), not the Google Gemini AI model. Gemini Exchange is operated by Gemini Trust Company, LLC.

## Source APIs

- REST API: https://docs.gemini.com/rest-api/
- WebSocket Market Data: https://docs.gemini.com/websocket-api/
- GitHub: https://github.com/gemini-exchange

## Schema Overview

The GraphQL schema provides a unified query interface over Gemini's REST and WebSocket APIs, covering:

### Market Data Types

- **Symbol** — Trading pair identifier (e.g., `btcusd`, `ethusd`)
- **SymbolDetails** — Full metadata for a trading symbol including tick size, quote currency, min order size
- **Ticker** — Current best bid, best ask, and last trade price for a symbol (v1)
- **TickerV2** — Extended ticker with open, high, low, close, and 24h changes
- **OHLCV** — Open/High/Low/Close/Volume candle data for a given time period
- **OrderBook** — Current state of bids and asks for a symbol
- **OrderBookEntry** — Individual price level with price and quantity
- **Trade** — A single executed trade on the exchange
- **AuctionInfo** — Metadata about the daily auction for a symbol
- **AuctionHistory** — Historical auction results
- **CurrentAuction** — Live auction status including indicative price and quantity
- **PriceFeedRecord** — Price feed entry for a symbol
- **MarketStatus** — Current market open/closed status
- **SymbolStatus** — Status of a specific trading symbol

### Account Types

- **Account** — Top-level account object containing balances and settings
- **AccountBalance** — Available and on-hold balance for a currency
- **NotionalBalance** — Balance expressed in a notional currency (USD value)
- **Deposit** — Record of a crypto or fiat deposit
- **Withdrawal** — Record of a crypto or fiat withdrawal
- **Transfer** — Internal account transfer record
- **CryptoAddress** — Deposit address for a cryptocurrency
- **BankAccount** — Linked bank account for fiat operations
- **ApiSettings** — Account-level API configuration and permissions
- **APIKey** — Individual API key metadata and scope

### Order Types

- **Order** — A placed order with full metadata
- **OrderStatus** — Current status details for a submitted order
- **PastOrder** — Historical closed or cancelled order record
- **OrderExecution** — Fill or partial fill record tied to an order
- **CancelResult** — Result of a cancel order operation
- **OpenOrders** — List of currently active open orders
- **BulkCancel** — Result of a bulk cancel operation

### Fee Types

- **FeeSchedule** — Tiered fee schedule based on 30-day volume
- **Price** — A monetary amount with currency denomination

### Earn / Staking Types

- **Earn** — Gemini Earn program participation record
- **EarningRate** — Current interest rate for a currency in Earn
- **EarningHistory** — Historical earn interest payment record
- **Staking** — Proof-of-stake staking position
- **StakingBalance** — Staked balance and rewards for a currency

### Payment Types

- **GeminiPayCode** — Gemini Pay payment code for point-of-sale transactions

### Perpetuals / Futures Types

- **Perpetual** — Perpetual contract instrument details
- **FuturePosition** — Open futures or perpetual position
- **FutureOrder** — Order placed in the futures/perpetuals market
- **FutureBalance** — Account balance in the futures subaccount

### Clearing Types

- **Clearing** — Bilateral clearing trade submission
- **ClearingTrade** — Executed and settled clearing trade record
- **ClearingBroker** — Approved clearing counterparty/broker record

### Capital / Network Types

- **CapitalAccount** — Institutional capital account details
- **CapitalBalance** — Balance within a capital account by currency
- **NetworkInfo** — Blockchain network information for a currency (confirmations, fees)

### Utility Types

- **Heartbeat** — WebSocket heartbeat acknowledgment
- **Event** — Generic WebSocket event envelope

## Type Count

The schema defines **55 named types** (excluding scalar and enum types).

## Query Capabilities

### Public Queries (No Auth Required)

```graphql
symbols: [Symbol!]!
symbolDetails(symbol: String!): SymbolDetails
ticker(symbol: String!): Ticker
tickerV2(symbol: String!): TickerV2
ohlcv(symbol: String!, resolution: String!, limit: Int): [OHLCV!]!
orderBook(symbol: String!, limit_bids: Int, limit_asks: Int): OrderBook
trades(symbol: String!, limit_trades: Int, since: String): [Trade!]!
auctionInfo(symbol: String!): AuctionInfo
auctionHistory(symbol: String!, limit_auction_results: Int, since: String): [AuctionHistory!]!
currentAuction(symbol: String!): CurrentAuction
priceFeed: [PriceFeedRecord!]!
marketStatus: MarketStatus
networkInfo(currency: String!): NetworkInfo
```

### Private Queries (Auth Required)

```graphql
account: Account
balances: [AccountBalance!]!
notionalBalances(currency: String!): [NotionalBalance!]!
transfers(currency: String, limit_transfers: Int, timestamp: String): [Transfer!]!
deposits(currency: String, limit_transfers: Int, timestamp: String): [Deposit!]!
withdrawals(currency: String, limit_transfers: Int, timestamp: String): [Withdrawal!]!
cryptoDepositAddress(currency: String!, network: String): CryptoAddress
bankAccounts: [BankAccount!]!
openOrders: OpenOrders
pastOrders(symbol: String, limit_trades: Int, account: String): [PastOrder!]!
orderStatus(order_id: String!): OrderStatus
feeSchedule: FeeSchedule
earnRates: [EarningRate!]!
earnBalances: [Earn!]!
earnHistory(currency: String, since: String, until: String): [EarningHistory!]!
stakingBalances: [StakingBalance!]!
stakingHistory(currency: String, since: String, until: String): [Staking!]!
apiSettings: ApiSettings
apiKeys: [APIKey!]!
futurePositions: [FuturePosition!]!
futureOrders: [FutureOrder!]!
futureBalances: [FutureBalance!]!
clearingTrades(since: String, until: String): [ClearingTrade!]!
clearingBrokers: [ClearingBroker!]!
capitalAccounts: [CapitalAccount!]!
capitalBalances: [CapitalBalance!]!
geminiPayCode: GeminiPayCode
```

### Mutations

```graphql
placeOrder(symbol: String!, amount: String!, price: String, side: OrderSide!, type: OrderType!, options: [String]): Order
cancelOrder(order_id: String!): CancelResult
cancelAllSessionOrders: BulkCancel
cancelAllActiveOrders: BulkCancel
withdraw(currency: String!, address: String!, amount: String!): Withdrawal
earnDeposit(currency: String!, amount: String!): Earn
earnWithdrawal(currency: String!, amount: String!): Earn
heartbeat: Heartbeat
```

## Authentication

Gemini Exchange uses HMAC-SHA384 signed API key authentication. All private queries and mutations require:

- `X-GEMINI-APIKEY` header with your API key
- `X-GEMINI-PAYLOAD` header with a base64-encoded JSON payload
- `X-GEMINI-SIGNATURE` header with an HMAC-SHA384 signature

In a GraphQL context, these credentials would be passed via HTTP headers on every request.

## References

- Gemini Exchange REST API Docs: https://docs.gemini.com/rest-api/
- Gemini WebSocket API Docs: https://docs.gemini.com/websocket-api/
- Gemini Developer Portal: https://docs.gemini.com/
- Gemini Exchange GitHub: https://github.com/gemini-exchange
