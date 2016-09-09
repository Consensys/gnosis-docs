# createMarket
** Creates a new market instance in the market contract address with a initial funding,
a market fee and the related Market Maker contract **
`createMarket(market, eventHash, config, [marketAddress], callback)`

* market: `object`
```js
{
  fee: 'bigNumber', // values between 0-10000 representing percentage of 0-50%
  initialFunding: 'bigNumber', // token amount in Wei
  makerAddress: 'string' // Market Maker contract address
}
```

* eventHash: `string`
* config: `object`
* marketAddress: `string` (optional)
> Market contract address, where market will be created

* callback: `function`

# closeMarket
** Close the market, returning the initial funding to the investor and the
market fees. Can only be done by the investor.**   
`closeMarket(marketHash, config, [marketAddress], callback)`

* marketHash: `string`
* config: `object`
* marketAddress: `string`
* callback: `function`

# getMarketHashes
** Get raw response from Market contract for get market hashes of related events. **
`getMarketHashes(eventHashes, config, [marketAddress], callback)`

* eventHashes: `array of eventHashes`
* config: `object`
* marketAddress: `string`
* callback: `function`

# getMarketHashesProcessed
** Get related array of market hashes for given event hashes. **
`getMarketHashesProcessed(eventHashes, config, [marketAddress])`

* eventHashes: `array of eventHashes`
* config: `object`
* marketAddress: `string`

# getMarket
** Get market properties for given market hash. Raw response from contract. **
`getMarket(marketHash, config, [marketAddress], callback)`

* marketHash: `string`
* config: `object`
* marketAddress: `string`
* callback: `function`

# getMarkets
** Get markets properties for given markets hashes. Raw response from contract. **
`getMarkets(marketHashes, config, [marketAddress], callback)`

* marketHashes: `array of marketHashes`
* config: `object`
* marketAddress: `string`
* callback: `function`

# getMarketsProcessed
** Get object map of markets for given markets hashes. Returns a Promise **
`getMarketsProcessed(marketHashes, config, [marketAddress])`

* marketHashes: `array of marketHashes`
* config: `object`
* marketAddress: `string`

# withdrawFees
** Withdraws market fees from market contract to investor address **   
`withdrawFees(marketHash, config, [marketAddress], callback)`

* marketHash: `string`
* config: `object`
* marketAddress: `string` (optional)
* callback: `function`

# getShareDistribution
** Get share distribution of market for a given blockNumber **   
`getShareDistribution(marketHash, blockNumber, config, [marketAddress], callback)`

* marketHash: `string`
* blockNumber: `latest|Hex string`
* config: `object`
* marketAddress: `string`
* callback: `function`

# getShareDistributionWithTimestamp
** Get share distribution with timestamp of market for a given blockNumber **   
`getShareDistributionWithTimestamp(marketHash, blockNumber, config, [marketAddress], callback)`

* marketHash: `string`
* blockNumber: `latest|Hex string`
* config: `object`
* marketAddress: `string`
* callback: `function`

# buyShares
** Buy outcome shares for a given market with a max allowed price for buying **   
`buyShares(marketHash, outcomeIndex, numShares, maxTotalPrice, config, [marketAddress], callback)`

* marketHash: `string`
* outcomeIndex: `bigNumber`
* numShares: `bigNumber`
* maxTotalPrice: `bigNumber`
> max amount of tokens to pay for shares

* config: `object`
* marketAddress: `string`
* callback: `function`

# sellShares
** Sell outcome shares for a given market with a min allowed price for selling **
`sellShares(marketHash, outcomeIndex, numShares, minTotalPrice, config, [marketAddress], callback)`

* marketHash: `string`
* outcomeIndex: `bigNumber`
* numShares: `bigNumber`
* minTotalPrice: `bigNumber`
> min amount of tokens expected to receive of selling shares

* config: `object`
* marketAddress: `string`
* callback: `function`

# calcMarketFee
** Get tokens fee for a given amount of tokens. Returns a promise. **  
`calcMarketFee(marketHash, amount, config, marketAddress)`

* marketHash: `string`
* amount: `string`
* config: `object`
* marketAddress: `string`

# shortSellShares
** Buys all outcomes and sells all outcomes unless the one selected with an expected price for selling outcomes. **    
`shortSellShares(marketHash, outcomeIndex, numShares, moneyToEarn, config, [marketAddress], callback)`

* marketHash: `string`
* outcomeIndex: `bigNumber`
* numShares: `bigNumber`
* moneyToEarn: `bigNumber`
> amount of tokens expected to receive of selling all outcomes unless the one selected

* config: `object`
* marketAddress: `string`
* callback: `function`
