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
## Options structure
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

# Main chain configuration
```js
{  
  addresses: {
    defaultMarket: '0x6ca7f214ab2ddbb9a8e1a1e2c8550e3164e9dba5',
    defaultMarketMaker: '0x8695e5e79dab06fbbb05f445316fa4edb0da30f0',
    etherToken: '0x92f1dbea03ce08225e31e95cc926ddbe0198e6f2',
    events: '0x5aae5c59d642e5fd45b427df6ed478b49d55fefd',
    ultimateOracle: '0x529c4cb814029b8bb32acb516ea3a4b07fdae350',
    lmsrMarketMaker: '0x8695e5e79dab06fbbb05f445316fa4edb0da30f0'
  },
  addressFilters: {
    oracle: '0x529c4cb814029b8bb32acb516ea3a4b07fdae350',
    investor: '0x0',
  },
  eventDescriptionFilters: {
    oracleAddresses: null,
    includeWhitelistedOracles: false,
    pageSize: 10
  },
  addressFiltersPostLoad: {
    marketMakers: ['0x8695e5e79dab06fbbb05f445316fa4edb0da30f0'],
    oracles: ['0x529c4cb814029b8bb32acb516ea3a4b07fdae350'],
    tokens: ['0x92f1dbea03ce08225e31e95cc926ddbe0198e6f2'],
  },
  gnosisServiceURL: 'https://www.gnosis.pm/api/',
  ethereumNodeURL: 'https://mainnet.infura.io'
}
```

# Morden configuration
```js
{
  addresses: {
    defaultMarket: '0x3b1da4a1ea5ccf9ec05eeb2318abcd7d4fe07455',
    defaultMarketMaker: '0xd3a0f8d4647342ce5c92ba989730308d69c6ca27',
    etherToken: '0x2cdd9fe0012e973b1bc0436e67475a890e3a717a',
    events: '0xcf18b7a386a015c1ac317f6c2368003997bb6a0c',
    ultimateOracle: '0xecf35d9475353c79f7a756c50bbe060efe0b545f',
    lmsrMarketMaker: '0xd3a0f8d4647342ce5c92ba989730308d69c6ca27'
  },
  addressFilters: {
    oracle: '0xecf35d9475353c79f7a756c50bbe060efe0b545f',
    investor: '0x0',
  },
  eventDescriptionFilters: {
    oracleAddresses: null,
    includeWhitelistedOracles: false,
    pageSize: 10
  },
  addressFiltersPostLoad: {
    marketMakers: ['0xd3a0f8d4647342ce5c92ba989730308d69c6ca27'],
    oracles: ['0xecf35d9475353c79f7a756c50bbe060efe0b545f'],
    tokens: ['0x2cdd9fe0012e973b1bc0436e67475a890e3a717a'],
  },
  gnosisServiceURL: 'https://beta.gnosis.pm/api/',
  ethereumNodeURL: 'https://morden.infura.io'
}
```

### Metamask/Mist integration
Metamask and mist injects a custom implementation of web3 in the browser in
`window.web3`.
You can check what wallet is using your user and pass it to the config:
```js
var customWeb3 = null;
if(window.web3){
  customWeb3 = new Web3(window.web3.currentProvider);
  if(typeof mist !== 'undefined') {
    // Is mist
  }
  else if(
    window.web3.currentProvider &&
    window.web3.currentProvider.constructor &&
    window.web3.currentProvider.constructor.name == "MetamaskInpageProvider"
  ){
    // Is metamask
  }
  else{
    // Is another wallet implementation
  }
}
```

Now you have an instance of web3 that can be passed to the config:
```js
const config = {
  ...
  config.web3 : customWeb3
  ...
}

```
