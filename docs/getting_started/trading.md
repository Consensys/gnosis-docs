The most easy way to interact with trading functions is throw the market object. You can also interact with:

* `Market maker`: for prices calculations with **gnosis.contracts.marketMaker** or **gnosis.marketMaker**
* `Market contract`: with **gnosis.contracts.market** you can buyShares, sellShares, shortSellShares...

# calcCostBuyingWithFee
```js
  market.calcCostsBuyingWithFee(
    new BigNumber('0'), // outcomeIndex
    new BigNumber('1e18'), // number of shares to buy
    function(e, cost){ // callback

    }
  ).call();
```
In gnosis.js functions that interact with blockchain like this one, and are using a eth_call internally,
always returns a request object that can be grouped for batch requesting.

You can also use the .call() method to do the request directly as shown above.

# calcEarningsSellingWithFees
```js
  market.calcEarningsSellingWithFees(
    new BigNumber('0'), // outcomeIndex
    new BigNumber('1e18'), // number of shares to buy
    function(e, earnings){ // callback

    }
  ).call();
```

# buyShares
```js
  market.buyShares(
    new BigNumber('0'), // outcomeIndex
    new BigNumber('1e18'), // number of shares to buy
    cost,
    function(e, receipt){
      // Called when buy shares transaction is mined
    }
  )
  .then(
    function(result){},
    function(error){}
  )
```

# sellShares
```js
  market.sellShares(
    new BigNumber('0'), // outcomeIndex
    new BigNumber('1e18'), // number of shares to sell
    earnings,
    function(e, receipt){
      // Called when sell shares transaction is mined
    }
  )
  .then(
    function(result){},
    function(error){}
  )
```
