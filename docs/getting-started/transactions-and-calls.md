# Transactions and calls

## Transactions
A transaction is a signed request that will be included in the blockchain as
proof of blockchain state change.
A transaction is needed when the action has an effect on the state of the blockchain,
for example buy shares, sell shares, create market...
We have two different responses from a function that sends a transaction:

1. **Promise:** Returns the result of doing eth_call before building the transaction. With the returned Promise we can know the output of the function.
2. **Callback:** The callback function called after the transaction is mined. We get the transaction result.

```js
gnosis.contracts.marketFactory.createMarket(
  ...
  function(e, receipt){
    // Called when market is created and transaction mined
  }
)
.then(
  function(createMarket){
    // createMarket.simulatedResult: marketHash
    // createMarket.txhash: Transaction hash
  }
)
```


## Calls
A call is an idempotent action over an Ethereum Node. We request the current
state of a function.
This can be done with two different ways:

1. **Now**: The function returns an object with a method `.call()`, sends directly the request
 and triggers the callback when it has response.
2. **Batch requests**: calls can be grouped and sent in batch with the [web3 batch](https://github.com/ethereum/wiki/wiki/JavaScript-API#batch-requests)

```js
// Batch request
const batch = web3.createBatch();
batch.add(
    market.calcEarningsSellingWithFees(..., callback)
);


// Direct
market.calcEarningsSellingWithFees(..., callback).call();
```
