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
    defaultMarketFactory: '0x1ec884fd25e73edd024153e5ced3051738c8fd63',

    // optional: Allows calculating of share prices without passing the
    // maker address
    defaultMarketMaker: '0xd4762520d0bd6b4013fcd916a3b2995666eb3a4a',

    // obligatory
    etherToken: '0x1912f977d4ed325f145644a7151f410aed75c85b',

    // obligatory
    eventFactory: '0x4f4c243aa1a7f9ffb12cec09d9d6cb8b0130a8ae',

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
    oracle: '0xb7ead0f8e08594b0337d4332554962b69a201cfc'
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
    defaultMarketFactory: '0x6ca7f214ab2ddbb9a8e1a1e2c8550e3164e9dba5',
    defaultMarketMaker: '0x8695e5e79dab06fbbb05f445316fa4edb0da30f0',
    etherToken: '0x92f1dbea03ce08225e31e95cc926ddbe0198e6f2',
    eventFactory: '0x5aae5c59d642e5fd45b427df6ed478b49d55fefd',
    ultimateOracle: '0x529c4cb814029b8bb32acb516ea3a4b07fdae350',
    lmsrMarketMaker: '0x8695e5e79dab06fbbb05f445316fa4edb0da30f0'
  },
  addressFilters: {
    oracle: '0x529c4cb814029b8bb32acb516ea3a4b07fdae350'
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
    defaultMarketFactory: '0x0daea8d631020db8450e9d469060ec4c3e463e21',
    defaultMarketMaker: '0x86e9e6cadfdb39e067d828a4513c98b34f57c005',
    etherToken: '0x271d50e46cf8a0681afcadaca333a9167cd862c9',
    eventFactory: '0xace10d12db82fcb445e55f2e3104cd3ad9c298d6',
    ultimateOracle: '0x69e06eb0ddb260c96a3e6e0f0a9b4970d6088a95',
    lmsrMarketMaker: '0x86e9e6cadfdb39e067d828a4513c98b34f57c005'
  },
  addressFilters: {
    oracle: '0x69e06eb0ddb260c96a3e6e0f0a9b4970d6088a95'
  },
  eventDescriptionFilters: {
    oracleAddresses: null,
    includeWhitelistedOracles: false,
    pageSize: 10
  },
  addressFiltersPostLoad: {
    marketMakers: ['0x86e9e6cadfdb39e067d828a4513c98b34f57c005'],
    oracles: ['0x69e06eb0ddb260c96a3e6e0f0a9b4970d6088a95'],
    tokens: [
      '0x271d50e46cf8a0681afcadaca333a9167cd862c9',
      '0xbe50ad81d86710a4833c3249d9e62b93088b1241'],
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
