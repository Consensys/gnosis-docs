# State properties
* `blockNumber`: actual blockNumber of state
* `eventDescriptions`: object map of event descriptions
* `events`: object map of events-on-chain
* `markets`: object map of markets grouped by market contract address
* `transactions`: object map of transactions made by the user
* `tokens`: tokens object map with balances, names, symbols and decimals
* `baseFee`: actual baseFee for gnosis
* `eventCount`: number of event descriptions there are at the API with current
              state filters

# state.buildState
** Builds the state retrieving event descriptions, events, markets, baseFee, eventShares and token balances.**   
`state.buildState(config, tokenAddresses, marketAddresses)`

* config: `object`
* tokenAddresses: `array`, token contracts addresses to get balances, symbol, name and decimals
* marketAddresses: `array`, market contracts addresses where get market objects.

```js
// Example for Morden network
gnosis.state.buildState(
  mordenConfig,
  ['0x2cdd9fe0012e973b1bc0436e67475a890e3a717a'], // Ether token address
  ['0x3b1da4a1ea5ccf9ec05eeb2318abcd7d4fe07455'] // Markets.sol address
)
.then(
  function(state){    
  }
)

// For later access
const state = gnosis.state.get(config);
```

# state.get
**Returns current state.**    
`state.get(config)`

* config: `object`

# state.updateState
**Update state market, shares and tokens properties with given filters**    
`updateState(config, filteredMarketHashes, tokenAddresses, marketAddresses)`

* config: `object`
* filteredMarketHashes: `array of marketHashes`
* tokenAddresses: `array of tokenAddresses`
* marketAddresses: `array of marketAddresses`

# state.updateEventDescriptions
**Returns a Promise with all event descriptions that match filters. Event descriptions are included in the state container too.**   
`state.updateEventDescriptions(config, filters)`

* config: `object`
* filters: `object` (optional)
> * creator_address: `string`, ethereum address of the description creator.
> * oracle_addresses: `string`, ethereum addresses comma separated of off-chain-oracles.
> * resolution_date_gt: `dateTime` [ISO 8641](https://en.wikipedia.org/wiki/ISO_8601)
> * description_hashes: `string`, description hashes comma separated.
> * include_whitelisted_oracles: `True|true|1`, includes whitelisted oracle's events.
> * page: `integer`
> * page_size: `integer`

# state.updateEvents
**Returns a Promise with all Events-on-chain that match address filters. Events-on-chain are included in the state container too.**   
`state.updateEvents(config, resolverAddress, tokenAddress, creatorAddress, filteredEventHashes)`

* config: `object`
* resolverAddress: `string` (optional)
> filter events resolved by oracle contract address    
* tokenAddress: `string` (optional)
> filter events by token contract address    
* creatorAddress: `string` (optional)
> filter events created by oracle account address     
* filteredEventHashes: `array of eventHashes` (optional)
> array of event hashes to update

# state.updateMarkets
**Returns a Promise with all markets that match address filters. Markets are included in the state container too.**   
`state.updateMarkets(config, marketContractAddress, investorAddress, filteredMarketHashes)`

* config: `object`
* marketContractAddress: `string` (optional)   
> market contract address    
* investorAddress: `string` (optional)
> investor account address   
* filteredMarketHashes: `array or marketHashes` (optional)   
> array of market hashes to update

# state.updateTokens
**Returns a Promise with all token balance, symbol, name and decimals for each tokenAddress**  
`state.updateTokens(tokenAddresses, config)`

* tokenAddresses: `array of tokenAddresses`
* config: `object`

# state.updateEventTokenShares
**Returns a Promise with all event shares balances**   
`state.updateEventTokenShares(forAddress, eventHashes, config)`

* forAddress: `string`
> owner of the shares    
* eventHashes: `array of eventHashes`   
* config: `config`

# state.updateBlocknumber
**Updates state block number**    
`state.updateBlocknumber(config)`

* config: `object`

# state.updateHistory
**Returns a Promise with an array of shares distributions over time**    
`state.updateHistory(marketAddress, marketHash, fromBlock, toBlock, sampleCount, config)`

* marketAddress: `string`
* marketHash: `string`
* fromBlock: `Hex string`
* toBlock: `Hex string`
* sampleCount: `integer`
> number of samples requested    
* config: `object`

# state.updateBaseFee
**Returns a Promise with the current base fee**    
`state.updateBaseFee(config)`

* config: `object`
