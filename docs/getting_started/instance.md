The first thing we need to do before using gnosis is **initialize** the config, in
this step we can pass an **options** object to gnosis, or use the default values:

```js
gnosis.config.initialize(
  configObject
)
.then(
  function(config){  
    // config will be used by gnosis functions  
  }
)
```

The options object has the following structure:
```js
{
  addresses: {
    // optional: Allows to do market operations without passing the
    // market address
    defaultMarket: '0x1ec884fd25e73edd024153e5ced3051738c8fd63',

    // optional: Allows calculating of share prices without passing the
    // maker address
    defaultMarketMaker: '0xd4762520d0bd6b4013fcd916a3b2995666eb3a4a',

    // obligatory
    etherToken: '0x1912f977d4ed325f145644a7151f410aed75c85b',

    // obligatory
    events: '0x4f4c243aa1a7f9ffb12cec09d9d6cb8b0130a8ae',

    // optional
    ultimateOracle: '0xb7ead0f8e08594b0337d4332554962b69a201cfc',
    // optional
    lmsrMarketMaker: '0xd4762520d0bd6b4013fcd916a3b2995666eb3a4a'
  },
  addressFiltersPostLoad: {
    marketMakers: ['0xd4762520d0bd6b4013fcd916a3b2995666eb3a4a'],
    oracles: ['0xb7ead0f8e08594b0337d4332554962b69a201cfc'],
    tokens: ['0x1ec884fd25e73edd024153e5ced3051738c8fd63'],
  },

  addressFilters: {
    // optional: Only loads events from blockchain, which are resolved by
    // given oracle
    oracle: '0xb7ead0f8e08594b0337d4332554962b69a201cfc',
    // optional: Only loads markets from blockchain, which are created by
    // given investor
    investor: null,
  },

  eventDescriptionFilters: {
    // resolutionDate: new Date(new Date().getTime() + 3600000*24*60),
    oracleAddresses: null,
    includeWhitelistedOracles: false,
    pageSize: 50// number of events returned by API for each page
  },

  defaultGas: 3000000,
  defaultGasPrice: new BigNumber('5e10'), // 50 gwei

  gnosisServiceURL: 'http://localhost:8050/api/',
  ethereumNodeURL: 'http://127.0.0.1:8545',

  persistTransactions: false,
  transactionConfirmCallback: null,
  newTransactionCallback: null,

  // an array of functions that each return a Promise. These functions will be
  // called in buildState and updateState calls.
  additionalUpdates: null,

  transactionsLoop: true, // transactions receipt loop
  requestBlockNumberTimeout: 5
};
```
