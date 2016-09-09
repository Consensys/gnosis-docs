# buyAllOutcomes
`buyAllOutcomes(eventHash, numShares, config, callback)`

Buy numberShares of all outcomes the event-on-chain has. In ranged events we buy for short and long shares.

* eventHash: `string`
> SHA3 Hash that identifies the event-on-chain

* numShares: `bigNumber`
> Numer of shares you want to buy of each outcome

* config: `object`

* callback: `function`

# redeemAllOutcomes
`redeemAllOutcomes(eventHash, numShares, config, callback)`

Sell numberShares of all outcome. You need to have the number of shares for each
outcome.

* eventHash: `string`
> SHA3 Hash that identifies the event-on-chain

* numShares: `bigNumber`
> Numer of shares you want to redeem of each outcome

* config: `object`

* callback: `function`

# redeemWinnings
`redeemWinnings(eventHash, config, callback)`

When event is resolved by the oracle/s if the user has shares of the winning outcome.
Will be allowed to redeem the tokens for that shares.

* eventHash: `string`
> SHA3 Hash that identifies the event-on-chain

* config: `object`

* callback: `function`

# createOffChainEvent
`createOffChainEvent(event, descriptionHash, feeSignatures, config, callback)`

Creates the event-on-chain using the Ultimate Oracle

* event: `object`
> See [event-on-chain object](/api_reference/Event)

* descriptionHash: `string`
* feeSignatures: `array`
```js
[
  {
    descriptionHash: 'string',
    message: 'bigNumber', // fee
    v: 'bigNumber',
    r: 'bigNumber'
    s: 'bigNumber'
  }
]
```
* config: `object`
* callback: `function`

# getEventHashes
`getEventHashes(descriptionHashes, config, callback)`

Returns raw response from events contract function

* descriptionHashes: `array of descriptionHashes`
* config: `object`
* callback: `function`

# getEventHashesProcessed
`getEventHashesProcessed(descriptionHashes, config)`

Returns an array of event hashes through a Promise.

* descriptionHashes: `array of descriptionHashes`
* config: `object`

# getEvents
`getEvents(eventHashes, resolverAddress, tokenAddress, creatorAddress, config, callback)`

Returns raw response from events contract function

* eventHashes: `array of eventHashes`
* resolverAddress: `string|null`

> Oracle contract address used as filter

* tokenAddress: `string|null`

> Token contract addrress used as filter

* creatorAddress: `string|null`

> Event creator account address  used as filter

* config: `object`

* callback: `function`

# getEventsProcessed
`getEventsProcessed(eventHashes, resolverAddress, tokenAddress, creatorAddress, config)`

Returns an object map of events through a Promise.

* eventHashes: `array of eventHashes`
* resolverAddress: `string|null`

> Oracle contract address used as filter

* tokenAddress: `string|null`

> Token contract addrress used as filter

* creatorAddress: `string|null`

> Event creator account address  used as filter

* config: `object`

# getEvent
`getEvent(eventHash, config, callback)`

* eventHash: `string`

* config: `object`

* callback: `function`


# getShares
`getShares(forAddress, eventHashes, config, callback)`

** Returns event shares for given event hashes. Raw response from contract.**

* forAddress: `string`
> Ethereum address of the account who owns the event shares

* eventHashes: `array of eventHashes`

* config: `object`

* callback: `function`

# getSharesProcessed
`getSharesProcessed(forAddress, eventHashes, config)`

** Returns event shares for given event hashes. Object map of tokens addresses through a Promise.**

* forAddress: `string`
> Ethereum address of the account who owns the event shares

* eventHashes: `array of eventHashes`

* config: `object`

# getBaseFee
`getBaseFee(config, callback)`

* config: `object`

* callback: `function`


# calcBaseFeeForShares
`calcBaseFeeForShares(shares, config)`

* shares: `bigNumber`
> Number of shares you are going to buy

* config: `object`

# calcBaseFee
`calcBaseFee(amount, config)`

* amount: `bigNumber`
> Amount of tokens you are going to spend

* config: `object`

# permitPermanentApproval
`permitPermanentApproval(spender, config, callback)`

* spender: `string`
> Account or contract address that will be allowed to spend sender event tokens.

* config: `object`

* callback: `function`

# isPermanentlyApproved
`isPermanentlyApproved(owner, spender, config, callback)`

* owner: `string`
> Account or contract address who owns the event tokens

* spender: `string`
> Account or contract allowed to spend event tokens

* config: `object`

* callback: `function`

# revokePermanentApproval
`revokePermanentApproval(allowedAddress, config, callback)`

* owner: `string`
> Account or contract address allowed to spend event tokens.

* config: `object`
* callback: `callback`
