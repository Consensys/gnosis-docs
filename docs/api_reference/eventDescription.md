There are two types of events:
* Discrete: has a discrete number of possible outcomes
* Ranged: has a continuous domain of pissible outcomes

## Discrete
```js
{
  title: 'string'
  description: 'string',
  tags: ['string'], (optional)
  sourceURL: 'url string',
  resolutionDate: 'datetime ISO',
  outcomes: ['string'],
  fee: 'bigNumber' (optional) // oracle fee charged for resolving the event
}
```

## Ranged
```js
{
  title: 'string'
  description: 'string',
  tags: ['string'], (optional)
  sourceURL: 'url string',
  resolutionDate: 'datetime ISO',
  unit: 'string', // domain unit for event outcome (e.g ETH, USD, EUR)
  decimals: 'integer' // number of representative decimals for event outcome
  fee: 'bigNumber' (optional) // oracle fee charged for resolving the event
}
```
