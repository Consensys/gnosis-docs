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
