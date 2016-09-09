## state.buildState
Builds the state retrieving event descriptions, events, markets, baseFee, eventShares and token balances.

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

```
### State properties
* `blockNumber`: actual blockNumber of state
* `eventDescriptions`: object map of event descriptions
* `events`: object map of events-on-chain
* `markets`: object map of markets grouped by market contract address
* `transactions`: object map of transactions made by the user
* `tokens`: tokens object map with balances, names, symbols and decimals
* `baseFee`: actual baseFee for gnosis
* `eventCount`: number of event descriptions there are at the API with current
              state filters
