As we had in event descriptions, we can have discrete and ranged events:

1. **Discrete:**
```js
{
  kind: 'discrete',
  outcomeCount: 'bigNumber',
  tokenAddress: 'string',
  resolverAddress: 'string',
}
```

2. **Ranged:**
```js
{
  kind: 'ranged',
  lowerBound: 'bigNumber', // Lower bound for outcome values
  upperBound: 'bigNumber', // Upper bound for outcome values
  outcomeCount: new BigNumber('2'), // short and long shares
  tokenAddress: 'string',
  resolverAddress: 'string',
}
```
