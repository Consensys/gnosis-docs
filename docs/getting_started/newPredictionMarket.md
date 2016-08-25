# Event description
We are gonna create an event description, the most human readable part of the
prediction market. This will be stored in the Gnosis API.

We can choose between ranged events and discrete events. Let's create a
discrete event about the ETH price:

```js
// event description object
const eventDescription = {
  title: "What will be the price in USD of ETH at the end of 2016?",
  description: "What will be the price of ETH in USD at the end of 2016? the price" +
               "Will be determined by https://www.kraken.com/charts at" +
               "2 January 2017, 14:00 UTC",
  tags: ["ethereum", "kraken"],
  sourceURL: "https://www.kraken.com/charts",
  resolutionDate: "2017-01-02T14:00:00.000Z",
  outcomes: ["<8$", ">=8$ <10$", ">=10$ <12$", ">=12$"],
  fee: new BigNumber('0')
}
```

We have all the information needed to create the event description, let's do the
request:

```js
gnosis.api.createEvent(
  eventDescription,
  config.account, // hex string 0x12323..., we choose the default one
  config // config object
)
.then(
  function(response){
    // response is the http response object (see axios https://github.com/mzabriskie/axios)
    // response.data has the following structure:
    response.data = {
      creationDate: "2016-08-24T09:48:04.858724Z",
      creatorAddress: "0x5dcd834cf776f47f138943e3466440009a2f2b00",
      descriptionHash:"0xcecfa7bd5a15da69166495b44386c35e1a1d70381476192e379666a2fb4d53d2",
      descriptionJSON: "{"title":"What will be the price in USD of ETH at the end of 2016?","description":"What will be the price of ETH in USD at the end of 2016? the priceWill be determined by https://www.kraken.com/charts at2 January 2017, 14:00 UTC","resolutionDate":"2017-01-02T14:00:00.000Z","sourceURL":"https://www.kraken.com/charts","tags":["ethereum","kraken"],"outcomes":["<8$",">=8$ <10$",">=10$ <12$",">=12$"]}",
      imageURL:"",
      offChainOracles: {
        0x5dcd834cf776f47f138943e3466440009a2f2b00: {
          fee: {          
            fee: 0, // fee value in wei
            r: "76313132358411676894858570476288595214390235035601740236150786169812569527480",
            s: "6893748021101910216468924035673437049986881004666946295153989969887086026472",
            v: 27
          },
          result: null,
          revisions: []
        }
      }
    }
  }
);
```

# Event on-chain
Now that we have stored all the event metadata in the Gnosis API, we are going
to create the event in the Ethereum Blockchain.
Take from the event description response, the following information:

* **descriptionHash**: is the SHA3 hash of descriptionJSON field.
* **kind**: 'discrete' or 'ranged'
* **outcomeCount**: 2 for ranged events and outcomes.length for discrete events
* **feeSignatures**: an array of one element. response.data.offChainOracles[oracleAddress].fee

We need two more parameters:

* **tokenAddress**: is the token contract address (e.g ETH '0x92f1dbea03ce08225e31e95cc926ddbe0198e6f2')
* **resolverAddress**: is the oracle contract address used to resolve the event. (e.g UltimateOracle '0x529c4cb814029b8bb32acb516ea3a4b07fdae350')

```js
const eventOnChain = {
  kind: "discrete",
  outcomeCount: 2,  
  tokenAddress: '0x92f1dbea03ce08225e31e95cc926ddbe0198e6f2',
  resolverAddress: '0x529c4cb814029b8bb32acb516ea3a4b07fdae350'
};

const feeSignatures = [
  {
    fee: 0,
    r: "76313132358411676894858570476288595214390235035601740236150786169812569527480",
    s: "6893748021101910216468924035673437049986881004666946295153989969887086026472",
    v: 27
  }
];

gnosis.contracts.events.createOffChainEvent(
  eventOnChain,
  "0xcecfa7bd5a15da69166495b44386c35e1a1d70381476192e379666a2fb4d53d2", // descriptionHash
  feeSignatures,
  config,
  function(e, receipt){
      console.log(receipt); // Transaction receipt, event was created and transactions was mined
  }
)
.then(
  function(createEvent){
    /*
    ** Create event transaction is well formed but it wasn't mined yet
    ** createEvent.simulatedResult == eventHash
    ** createEvent.txhash == transaction hash    
    */
  },
  function(e){
    // There was an error
  }
)
```

As you have noticed, there are to ways to get response of the creation:

1. **Callback**: It's called in last place, after the transaction is mined.
2. **Promise**: It's faster, but we have not certainty when it will be in the blockchain.

# Market
This is the final step, we open the market with an initial funding of tokens and
set the market fee.
This is the info needed:

1. eventHash: it's hash that identies the event. We already have it, is the
  value of createEvent.simulatedResult.
2. marketFee: percentage that the investor takes of trading actions.
Values between 0-50%, represented as 0-1000000.
3. initialFunding: amount of tokens the investor put into the market.
4. marketAddress: market contract address (e.g Markets.sol '0x8e007af2b8ee9d70e578503db5a1bcdabd5ce847')

```js
const market = {
  marketFee: new BigNumber('0'),
  initialFunding: new BigNumber('1e18') // 10 ETH  
}
```
