# livecoin-api

Simple LiveCoin API wrapper for Node.js

LiveCoin API documentation can be found at <https://www.livecoin.net/api/common>

## Installation

  `npm install livecoin-api`

## Usage

```js
const LiveCoin = require('livecoin-api');
const client = new LiveCoin('key here', 'secret here');

client.getTicker('btc', 'usd').then(console.log).catch(console.error);
client.getAllTickers().then(console.log).catch(console.error);
client.getCurrencies().then(console.log).catch(console.error);
```

See examples.js for more examples.

## Tests

  `npm test`

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

-   [LiveCoin](#livecoin)
    -   [login](#login)
    -   [getTicker](#getticker)
    -   [getAllTickers](#getalltickers)
    -   [getLastTrades](#getlasttrades)
    -   [getOrders](#getorders)
    -   [getAllOrders](#getallorders)
    -   [getBidAndAsk](#getbidandask)
    -   [getAllBidsAndAsks](#getallbidsandasks)
    -   [getRestrictions](#getrestrictions)
    -   [getCurrencies](#getcurrencies)
    -   [getUserTrades](#getusertrades)
    -   [getClientOrders](#getclientorders)
    -   [getUserOrder](#getuserorder)
    -   [getBalances](#getbalances)
    -   [getBalance](#getbalance)
    -   [getTransactions](#gettransactions)
    -   [getNumTransactions](#getnumtransactions)
    -   [getTradingFee](#gettradingfee)
    -   [getTradingFeeAndVolume](#gettradingfeeandvolume)
    -   [buyLimit](#buylimit)
    -   [sellLimit](#selllimit)
    -   [buyMarket](#buymarket)
    -   [sellMarket](#sellmarket)
    -   [cancelLimit](#cancellimit)
    -   [getAddress](#getaddress)
    -   [withdraw](#withdraw)
    -   [toPayeer](#topayeer)
    -   [toCapitalist](#tocapitalist)
    -   [toAdvcash](#toadvcash)
    -   [toYandex](#toyandex)
    -   [toQiwi](#toqiwi)
    -   [toBankCard](#tobankcard)
    -   [toMastercard](#tomastercard)
    -   [toOkpay](#tookpay)
    -   [toPerfectMoney](#toperfectmoney)
    -   [makeVoucher](#makevoucher)
    -   [getVoucherAmount](#getvoucheramount)
    -   [redeemVoucher](#redeemvoucher)

### LiveCoin

Class representing LiveCoin client

**Parameters**

-   `apiKey`   (optional, default `''`)
-   `apiSecret`   (optional, default `''`)

#### login

Set client's API key and secret after constructing the object

**Parameters**

-   `apiKey` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** API key generated from LiveCoin
-   `apiSecret` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** API secret generated from LiveCoin

**Examples**

```javascript
client.login('key here', 'secret here');
```

#### getTicker

Get ticker information

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with

**Examples**

```javascript
client.getTicker('btc', 'usd').then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** ticker information

#### getAllTickers

Get all tickers' information

**Examples**

```javascript
client.getAllTickers().then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** all tickers' information

#### getLastTrades

Get information on most recent trades

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options for the query (optional, default `{}`)
    -   `options.minOrHr` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** if true, info from minute, else hour
    -   `options.type` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** must be either BUY or SELL

**Examples**

```javascript
client.getLastTrades('btc', 'usd').then(console.log);
 client.getLastTrades('eth', 'btc', {minOrHr: true}).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on most recent trades

#### getOrders

Get information on orders

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options for the query (optional, default `{}`)
    -   `options.groupByPrice` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** if true, groups by price
    -   `options.depth` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** maximum number of orders to return

**Examples**

```javascript
client.getOrders('btc', 'usd').then(console.log).catch(console.log);
 client.getOrders('eth', 'btc', {groupByPrice: true, depth: 4}).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on orders

#### getAllOrders

Get information on orders for all exchanges

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options for the query (optional, default `{}`)
    -   `options.groupByPrice` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** if true, groups by price
    -   `options.depth` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** maximum number of orders to return

**Examples**

```javascript
client.getAllOrders().then(console.log).catch(console.log);
 client.getAllOrders({groupByPrice: true, depth: 4}).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on orders for all exchanges

#### getBidAndAsk

Get maximum bid and minimum ask for a currency

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with

**Examples**

```javascript
client.getBidAndAsk('btc', 'usd').then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** maximum bid and minimum ask

#### getAllBidsAndAsks

Get maximum bid and minimum ask for all currencies

**Examples**

```javascript
client.getAllBidsAndAsks().then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** maximum bid and minimum ask for all currencies

#### getRestrictions

Get minimum amount to open order for all currencies

**Examples**

```javascript
client.getRestrictions().then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** minimum amount to open order for all currencies

#### getCurrencies

Get minimum amount to open order for all currencies

**Examples**

```javascript
client.getCurrencies().then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** minimum amount to open order for all currencies

#### getUserTrades

Get information on user's recent trades, requires API key and secret

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options for the query (optional, default `{}`)
    -   `options.currencyPair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** exchange in the format BTC/USD
    -   `options.orderDesc` **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)?** if true, new orders will be shown first
    -   `options.limit` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** number of items per page
    -   `options.offset` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** page offset

**Examples**

```javascript
client.getUserTrades({orderDesc: true, limit: 4}).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on user's trades

#### getClientOrders

Get information on user's orders, requires API key and secret

**Parameters**

-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options for the query (optional, default `{}`)
    -   `options.currencyPair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** exchange in the format BTC/USD
    -   `options.openClosed` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** type of order, e.g 'ALL' or 'OPEN'
    -   `options.issuedFrom` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** start date in UNIX format
    -   `options.issuedTo` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** end date in UNIX format
    -   `options.startRow` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** sequence number of first record
    -   `options.endRow` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** sequence number of last record

**Examples**

```javascript
client.getClientOrders({openClosed: 'CANCELLED', startRow: 2}).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on user's orders

#### getUserOrder

Get order information, requires API key and secret

**Parameters**

-   `orderId` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** ID of the order, e.g. 88504958

**Examples**

```javascript
client.getUserOrder(88504958).then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** order information

#### getBalances

Get information on balances, requires API key and secret

**Parameters**

-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** will return all balances if not given, e.g. USD (optional, default `''`)

**Examples**

```javascript
client.getBalances().then(console.log).catch(console.error);
```

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)>** information on balances

#### getBalance

Get information on balance for a currency, requires API key and secret

**Parameters**

-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency to get balance for, e.g. BTC

**Examples**

```javascript
client.getBalance('BTC').then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on balances

#### getTransactions

Get list of transactions, requires API key and secret

**Parameters**

-   `start` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** start date in UNIX format
-   `end` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** end date in UNIX format
-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options for the query (optional, default `{}`)
    -   `options.types` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** type of order, e.g 'BUY' or 'DEPOSIT'
    -   `options.limit` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** max number of results
    -   `options.offset` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** first index

**Examples**

```javascript
client.getTransactions('1409920436000', '1409920636000', 
 {types: 'BUY', limit: 2}).then(console.log).catch(console.error);
```

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)>** list of transactions in the date range

#### getNumTransactions

Get number of transactions, requires API key and secret

**Parameters**

-   `start` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** start date in UNIX format
-   `end` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** end date in UNIX format
-   `types`  

**Examples**

```javascript
client.getNumTransactions('1409920436000', '1409920636000', 'BUY').then(console.log);
```

Returns **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** number of transactions in the date range

#### getTradingFee

Get customer's trading fee

**Examples**

```javascript
client.getTradingFee().then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** trading fee

#### getTradingFeeAndVolume

Get customer's trading fee and volume

**Examples**

```javascript
client.getTradingFeeAndVolume().then(console.log).catch(console.error);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** trading fee and volume

#### buyLimit

Make a buy limit order

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `price` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** price of currency
-   `quantity` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount of currency to buy

**Examples**

```javascript
client.buyLimit('btc', 'usd', 10000, 0.1).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** order ID

#### sellLimit

Make a sell limit order

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `price` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** price of currency
-   `quantity` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount of currency to sell

**Examples**

```javascript
client.sellLimit('btc', 'usd', 10000, 0.1).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** order ID

#### buyMarket

Make a buy market order

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `quantity` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount of currency to buy

**Examples**

```javascript
client.buyMarket('btc', 'usd', 0.1).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** order ID

#### sellMarket

Make a sell market order

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `quantity` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount of currency to sell

**Examples**

```javascript
client.sellMarket('btc', 'usd', 0.1).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** order ID

#### cancelLimit

Cancel order

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `pair` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency being traded with
-   `orderId` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** ID of order to cancel

**Examples**

```javascript
client.cancelLimit('btc', 'usd', 1111).then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** order ID

#### getAddress

Get wallet address for a currency

**Parameters**

-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker

**Examples**

```javascript
client.getAddress('btc').then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** wallet address

#### withdraw

Withdraw to wallet address

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address

**Examples**

```javascript
client.withdraw(1, 'usd', '1MfTTxGnBBgvyk9477hWurosfqj8MZKkAG')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toPayeer

Withdraw to Payeer account

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address
-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options object (optional, default `{}`)
    -   `options.protect` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** protection of payment
    -   `options.protect_code` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** protect code
    -   `options.protect_period` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** protect period in days

**Examples**

```javascript
client.toPayeer(1, 'usd', '1MfTTxGnBBgvyk9477hWurosfqj8MZKkAG')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toCapitalist

Withdraw to Capitalist account

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be USD, EUR, or RUR only
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address

**Examples**

```javascript
client.toCapitalist(1, 'USD', 'U0000001')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toAdvcash

Withdraw to Advcash account

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be USD, EUR, or RUR only
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address

**Examples**

```javascript
client.toAdvcash(1, 'USD', 'U123456789012')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toYandex

Withdraw to Yandex account

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be RUR only
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address

**Examples**

```javascript
client.toYandex(1, 'RUR', '410011234567890')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toQiwi

Withdraw to Qiwi account

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be RUR only
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address including country code without '+'

**Examples**

```javascript
client.toQiwi(1, 'RUR', '79036660099')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toBankCard

Withdraw to bank card

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be USD, EUR, or RUR only
-   `account` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** bank account number

**Examples**

```javascript
client.toBankCard(1, 'USD', '5567025017512543', '09', '18')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toMastercard

Withdraw to Mastercard card

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be USD or EUR only
-   `cardNumber` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Card number
-   `cardHolder` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Cardholder name
-   `cardHolderCountry` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Cardholder country in ISO 3166-1 alpha-2 format (e.g. RU)
-   `cardHolderCity` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Cardholder city
-   `cardHolderDOB` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Cardholder DOB in YYYY-MM-DD format
-   `cardHolderMobilePhone` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** Cardholder phone number including country code without '+'

**Examples**

```javascript
client.toMastercard(1, 'USD', '1234123412341234',
   'John Smith', 'US', 'Dallas', '1968-05-15', '79036660099')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toOkpay

Withdraw to Okpay card

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `currency` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** can be USD, EUR, or RUR only
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** account wallet
-   `invoice` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** optional invoice number (optional, default `''`)

**Examples**

```javascript
client.toOkpay(1, 'USD', 'OK123456789')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### toPerfectMoney

Withdraw to PerfectMoney account

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `wallet` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** wallet address
-   `options` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)?** options object (optional, default `{}`)
    -   `options.protect_code` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** protect code
    -   `options.protect_period` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)?** protect period in days

**Examples**

```javascript
client.toPerfectMoney(1, 'usd', '1MfTTxGnBBgvyk9477hWurosfqj8MZKkAG')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on withdrawal

#### makeVoucher

Creates a voucher

**Parameters**

-   `amount` **[number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** amount to withdraw
-   `ticker` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** currency ticker
-   `description` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)?** purpose of payment (optional, default `''`)

**Examples**

```javascript
client.makeVoucher(1, 'usd', 'need a voucher')
 .then(console.log);
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** voucher code

#### getVoucherAmount

Get voucher amount from voucher code

**Parameters**

-   `voucherCode` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** voucher code

**Examples**

```javascript
client.getVoucherAmount('LVC-USD-12345678-87654321-ABCDEFGI-ABCD1234')
 .then(console.log);
```

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** voucher amount

#### redeemVoucher

Redeem voucher from code

**Parameters**

-   `voucherCode` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** voucher code

**Examples**

```javascript
client.redeemVoucher('LVC-USD-12345678-87654321-ABCDEFGI-ABCD1234')
 .then(console.log);
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** information on voucher redeeming

## Contributing

Contributions welcome!

```shell
# 1. Fork the repo and clone it to your computer
$ git clone https://github.com/your-username/livecoin-api.git
$ cd livecoin-api

# 2. Connect your fork with this repo to stay up to date on any changes
$ git remote add upstream https://github.com/abhinavk99/livecoin-api.git

# 3. Make your feature branch
$ git checkout -b new-feature

# 4. Test your changes
$ npm test

# 5. Add and commit the changes you made
$ git add .
$ git commit -m "Added new feature"

# 6. Push to your branch
$ git push origin new-feature

# 7. Create a pull request on GitHub
```

Alternatively, feel free to open [an issue](https://github.com/abhinavk99/livecoin-api/issues).
