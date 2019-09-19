# CPUfinex API Docs

# User API v2

***API startpoint:*** https://cpufinex.com/api/v2/trade/

### Security
**Bearer**  

|apiKey|*API Key*|
|---|---|
|Name|JWT|
|In|header|

# Public API

## Timestamp

#### https://cpufinex.com/api/v2/trade/public/timestamp

#### GET
#### Description:

Get server current time, in seconds since Unix epoch.

#### Responses

| Code | Description |
| ---- | ----------- |
| 200 | Get server current time, in seconds since Unix epoch. |

## Summary Endpoint

#### https://cpufinex.com/api/v2/trade/public/summary

#### GET
#### Description:

The summary endpoint is to provide the overview of market data for all tickers on the exchange.

#### Preview

```json
{ 
   "BTCUSDT":{ 
      "baseVolume":"13.5879444",
      "high24hr":"10261.0",
      "highestBid":"10240.0",
      "isFrozen":0,
      "last":"10237.0",
      "low24hr":"10220.0",
      "lowestAsk":"10246.0",
      "percentChange":"-0.17%",
      "quoteVolume":"139205.93465899"
   }
}
```

#### Assets response descriptions.

| Name | Type | Description
| ---- | ---- | ----------- |
| baseVolume | boolean | 24 hour trading volume in base pair volume. |
| high24hr | boolean | 24 hour highest known price of the market. |
| highestBid | boolean | 24 hour highest bid price of the market. |
| isFrozen | integer | Indicates if the market is currently enabled (1) or disabled (0). |
| last | boolean | The price of the last executed order. |
| low24hr | boolean | 24 hour lowest known price of the market. |
| lowestAsk | boolean | 24 hour lowest bid price of the market. |
| percentChange | decimal | Percentage of price changed in 24 hours. |
| quoteVolume | decimal | 24 hour trading volume in quote pair volume. |

## Assets

#### https://cpufinex.com/api/v2/trade/public/asset

#### GET
#### Description:

The assets endpoint is to provide a detailed summary for each currency available on the exchange.

#### Preview

```json
{ 
   "btc":{ 
      "name":"Bitcoin",
      "unified_cryptoasset_id":1,
      "can_withdraw":true,
      "can_deposit":true,
      "min_withdraw":"0.002",
      "max_withdraw":"2.0",
      "maker_fee":0.01,
      "taker_fee":0.01
   },
   "ltc":{ 
      "name":"Litecoin",
      "unified_cryptoasset_id":2,
      "can_withdraw":true,
      "can_deposit":true,
      "min_withdraw":"0.02",
      "max_withdraw":"20.0",
      "maker_fee":0.01,
      "taker_fee":0.01
   }
}
```

#### Assets response descriptions.

| Name | Type | Description
| ---- | ---- | ----------- |
| name | string | Name of cryptocurrency |
| [unified_cryptoasset_id](https://pro-api.coinmarketcap.com/v1/cryptocurrency/map?CMC_PRO_API_KEY=UNIFIED-CRYPTOASSET-INDEX&listing_status=active) | integer | Unique ID of cryptocurrency assigned by CoinMarketCap. |
| can_withdraw | boolean | Identifies whether withdraws are enabled or disabled. |
| can_deposit | boolean | Identifies whether deposits are enabled or disabled. |
| min_withdraw | decimal | Identifies the single minimum withdraw amount of a cryptocurrency. |
| max_withdraw | decimal | Identifies the single maximum withdraw amount of a cryptocurrency. |
| maker_fee | decimal | Fees applied when liquidity is added to the order book. |
| taker_fee | decimal | Fees applied when liquidity is removed from the order book. |


## Tickers

#### https://cpufinex.com/api/v2/trade/public/ticker

#### GET
#### Description:

The ticker endpoint is to provide a 24-hour pricing and volume summary for each market pair available on the exchange.

#### Preview

```json
{ 
   "btcusdt":{ 
      "base_id":1,
      "quote_id":825,
      "last_price":"10330.0",
      "quote_volume":"722989.94601353",
      "base_volume":"69.98940837",
      "isFrozen":0
   },
   "ethusdt":{ 
      "base_id":1027,
      "quote_id":825,
      "last_price":"194.21",
      "quote_volume":"520199.6604528334",
      "base_volume":"2738.72039554",
      "isFrozen":0
   }
}
```

#### Assets response descriptions.

| Name | Type | Description
| ---- | ---- | ----------- |
| base_id | integer | The base pair Unified Cryptoasset ID. |
| quote_id | integer | The quote pair Unified Cryptoasset ID. |
| last_price | boolean | The price of the last executed order. |
| base_volume | boolean | 24 hour trading volume in base pair volume. |
| quote_volume | decimal | 24 hour trading volume in quote pair volume. |
| isFrozen | integer | Indicates if the market is currently enabled (1) or disabled (0). |


## Orderbook

#### https://cpufinex.com/api/v2/trade/public/orderbook/{market}

#### GET
#### Description:

The order book endpoint is to provide a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair.

#### Preview

```json
{ 
   "timestamp":1568626332,
   "asks":[ 
      [ 
         "10501.0",
         "0.55170562"
      ],
      [ 
         "10500.0",
         "3.8798151"
      ],
      [ 
         "10499.0",
         "0.78020624"
      ]
   ],
   "bids":[ 
      [ 
         "10240.0",
         "0.0112332"
      ],
      [ 
         "10239.0",
         "0.02486108"
      ]
   ]
}
```

#### Assets response descriptions.

| Name | Type | Description
| ---- | ---- | ----------- |
| timestamp | timestamp | Unix timestamp in milliseconds for when the last updated time occurred. |
| bids | decimal | An array containing 2 elements. The offer price and quantity for each bid order. |
| asks | decimal | An array containing 2 elements. The ask price and quantity for each ask order. |


## Trades

#### https://cpufinex.com/api/v2/trade/public/trades/{market}

#### GET
#### Description:

The trades endpoint is to return data on all recently completed trades for a given market pair.

#### Preview

```json
[ 
   { 
      "tradeID":318613,
      "price":"10332.0",
      "base_volume":"0.06906451",
      "quote_volume":"713.57451732",
      "trade_timestamp":1568626351,
      "type":"sell"
   },
   { 
      "tradeID":318533,
      "price":"10332.0",
      "base_volume":"0.07495705",
      "quote_volume":"774.45624060",
      "trade_timestamp":1568626231,
      "type":"sell"
   }
]
```

#### Assets response descriptions.

| Name | Type | Description
| ---- | ---- | ----------- |
| trade_id | integer | A unique ID associated with the trade for the currency pair transaction. |
| price | decimal | Transaction price in base pair volume. |
| base_volume | decimal | Transaction amount in base pair volume. |
| quote_volume | decimal | Transaction amount in quote pair volume.e. |
| trade_timestamp | timestamp | Unix timestamp in milliseconds for when the transaction occurred.. |
| type | string | Used to determine whether or not the transaction originated as a buy or sell.* |

* Buy – Identifies an ask was removed from the order book. Sell – Identifies a bid was removed from the order book.

## Private API (User API)

### https://cpufinex.com/api/v2/trade/account/balances/{currency}

#### GET
##### Description:

Get user account by currency

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | path | The currency code. | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get user account by currency | [Account](#account) |

### https://cpufinex.com/api/v2/trade/account/balances

#### GET
##### Description:

Get list of user accounts

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get list of user accounts | [ [Account](#account) ] |

### https://cpufinex.com/api/v2/trade/account/deposit_address/{currency}

#### GET
##### Description:

Returns deposit address for account you want to deposit to by currency. The address may be blank because address generation process is still in progress. If this case you should try again later.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | path | The account you want to deposit to. | Yes | string |
| address_format | query | Address format legacy/cash | No | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Returns deposit address for account you want to deposit to by currency. The address may be blank because address generation process is still in progress. If this case you should try again later. | [Deposit](#deposit) |

### https://cpufinex.com/api/v2/trade/account/deposits/{txid}

#### GET
##### Description:

Get details of specific deposit.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| txid | path | Deposit transaction id | Yes | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get details of specific deposit. | [Deposit](#deposit) |

### https://cpufinex.com/api/v2/trade/account/deposits

#### GET
##### Description:

Get your deposits history.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | Currency code | No | string |
| state | query |  | No | string |
| limit | query | Number of deposits per page (defaults to 100, maximum is 100). | No | integer |
| page | query | Page number (defaults to 1). | No | integer |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get your deposits history. | [ [Deposit](#deposit) ] |

### https://cpufinex.com/api/v2/trade/account/withdraws

#### POST
##### Description:

Creates new crypto withdrawal.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| otp | formData | OTP to perform action | Yes | integer |
| rid | formData | Wallet address on the Blockchain. | Yes | string |
| currency | formData | The currency code. | Yes | string |
| amount | formData | The amount to withdraw. | Yes | double |

##### Responses

| Code | Description |
| ---- | ----------- |
| 201 | Creates new crypto withdrawal. |

#### GET
##### Description:

List your withdraws as paginated collection.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| currency | query | Currency code. | No | string |
| limit | query | Number of withdraws per page (defaults to 100, maximum is 100). | No | integer |
| page | query | Page number (defaults to 1). | No | integer |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | List your withdraws as paginated collection. | [ [Withdraw](#withdraw) ] |

### https://cpufinex.com/api/v2/trade/market/trades

#### GET
##### Description:

Get your executed trades. Trades are sorted in reverse creation order.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query |  | No | string |
| limit | query | Limit the number of returned trades. Default to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| timestamp | query | An integer represents the seconds elapsed since Unix epoch.If set, only trades executed before the time will be returned. | No | integer |
| order_by | query | If set, returned trades will be sorted in specific order, default to 'desc'. | No | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get your executed trades. Trades are sorted in reverse creation order. | [ [Trade](#trade) ] |

### https://cpufinex.com/api/v2/trade/market/orders/cancel

#### POST
##### Description:

Cancel all my orders.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| side | formData | If present, only sell orders (asks) or buy orders (bids) will be canncelled. | No | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Cancel all my orders. | [Order](#order) |

### https://cpufinex.com/api/v2/trade/market/orders/{id}/cancel

#### POST
##### Description:

Cancel an order.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes | integer |

##### Responses

| Code | Description |
| ---- | ----------- |
| 201 | Cancel an order. |

### https://cpufinex.com/api/v2/trade/market/orders

#### POST
##### Description:

Create a Sell/Buy order.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | formData |  | Yes | string |
| side | formData |  | Yes | string |
| volume | formData |  | Yes | double |
| ord_type | formData |  | No | string |
| price | formData |  | Yes | double |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 201 | Create a Sell/Buy order. | [Order](#order) |

#### GET
##### Description:

Get your orders, results is paginated.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| market | query |  | No | string |
| state | query | Filter order by state. | No | string |
| limit | query | Limit the number of returned orders, default to 100. | No | integer |
| page | query | Specify the page of paginated results. | No | integer |
| order_by | query | If set, returned orders will be sorted in specific order, default to "desc". | No | string |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get your orders, results is paginated. | [ [Order](#order) ] |

### https://cpufinex.com/api/v2/trade/market/orders/{id}

#### GET
##### Description:

Get information of specified order.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| id | path |  | Yes | integer |

##### Responses

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Get information of specified order. | [Order](#order) |

### Models


#### Trade

Get your executed trades. Trades are sorted in reverse creation order.

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | string | Trade ID. | No |
| price | double | Trade price. | No |
| volume | double | Trade volume. | No |
| funds | double | Trade funds. | No |
| market | string | Trade market id. | No |
| created_at | string | Trade create time in iso8601 format. | No |
| taker_type | string | Trade maker order type (sell or buy). | No |
| side | string | Trade side. | No |
| order_id | integer | Order id. | No |

#### OrderBook

Get the order book of specified market.

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| asks | [ [Order](#order) ] | Asks in orderbook | No |
| bids | [ [Order](#order) ] | Bids in orderbook | No |

#### Order

Get your orders, results is paginated.

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | integer | Unique order id. | No |
| side | string | Either 'sell' or 'buy'. | No |
| ord_type | string | Type of order, either 'limit' or 'market'. | No |
| price | double | Price for each unit. e.g.If you want to sell/buy 1 btc at 3000 usd, the price is '3000.0' | No |
| avg_price | double | Average execution price, average of price in trades. | No |
| state | string | One of 'wait', 'done', or 'cancel'.An order in 'wait' is an active order, waiting fulfillment;a 'done' order is an order fulfilled;'cancel' means the order has been canceled. | No |
| market | string | The market in which the order is placed, e.g. 'btcusd'.All available markets can be found at /api/v2/markets. | No |
| created_at | string | Order create time in iso8601 format. | No |
| updated_at | string | Order updated time in iso8601 format. | No |
| origin_volume | double | The amount user want to sell/buy.An order could be partially executed,e.g. an order sell 5 btc can be matched with a buy 3 btc order,left 2 btc to be sold; in this case the order's volume would be '5.0',its remaining_volume would be '2.0', its executed volume is '3.0'. | No |
| remaining_volume | double | The remaining volume, see 'volume'. | No |
| executed_volume | double | The executed volume, see 'volume'. | No |
| trades_count | integer | Count of trades. | No |
| trades | [ [Trade](#trade) ] | Trades wiht this order. | No |

#### Account

Get list of user accounts

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| currency | string | Currency code. | No |
| balance | double | Account balance. | No |
| locked | double | Account locked funds. | No |

#### Deposit

Get your deposits history.

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | integer | Unique deposit id. | No |
| currency | string | Deposit currency id. | No |
| amount | double | Deposit amount. | No |
| fee | double | Deposit fee. | No |
| txid | string | Deposit transaction id. | No |
| confirmations | integer | Number of deposit confirmations. | No |
| state | string | Deposit state. | No |
| created_at | string | The datetime when deposit was created. | No |
| completed_at | string | The datetime when deposit was completed.. | No |

#### Withdraw

List your withdraws as paginated collection.

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| id | integer | The withdrawal id. | No |
| currency | string | The currency code. | No |
| type | string | The withdrawal type | No |
| amount | string | The withdrawal amount | No |
| fee | double | The exchange fee. | No |
| blockchain_txid | string | The withdrawal transaction id. | No |
| rid | string | The beneficiary ID or wallet address on the Blockchain. | No |
| state | string | The withdrawal state. | No |
| confirmations | integer | Number of confirmations. | No |
| created_at | string | The datetimes for the withdrawal. | No |
| updated_at | string | The datetimes for the withdrawal. | No |
| done_at | string | The datetime when withdraw was completed | No |

#### Member

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| uid | string | Member UID. | No |
| email | string | Member email. | No |
| accounts | [ [Account](#account) ] | Member accounts. | No |
