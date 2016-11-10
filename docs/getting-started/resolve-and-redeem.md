In order to resolve the event with the Ultimate Oracle there are two steps:

1. **Publish outcome.** Publish oracle's winning outcome in the blockchain.
In [ultimateOracle](/reference/contracts/ultimate-oracle) you have two
functions: **setOutcome** and **setOutcomeWithSignature**.
```js
gnosis.contracts.ultimateOracle.setOutcome(
  eventIdentifier,
  descriptionHash,
  outcomeIndex,
  oracleAddress,
  config,
  function(e, receipt){
    // Outcome set
  }
)
```

2. **Wait challenge period.** Winning outcome won't be resolved until challenge
period is over (12h if there are no challenges, 24h if there are).


After event is resolved, users can [redeem their winning outcomes](/reference/contracts/event-factory) if they have shares
for the winning outcome.
```js
gnosis.contracts.eventFactory.redeemWinnings(
  eventHash,
  config,
  function(e, receipt){
    // Shares redeemed
  }
)
```
