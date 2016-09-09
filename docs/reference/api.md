# createEvent
`createEvent(event, oracleAddress, config)`

  * event: `object`
  > Discrete or Ranged see [Event Description](/reference/eventDescription)

  * oracleAddress: `string`
  > Ethereum address used to sign the event description. You must own this address

  * config: `object`


# subscribeOracleToEvent
`subscribeOracleToEvent(givenFee, descriptionHash, oracleAddress, email, config)`

* givenFee: `bigNumber`.
> Fee oracle charges for resolving the event.

* descriptionHash: `string`
> DescriptionHash that identifies the event.

* email: `email`
> Email to notify oracle when event needs to be resolved.

* config: `object`


# postResult
`postResult(resultObject, oracleAddress, config)`

* resultObject: `object`.

```js
{
  result: 'bigNumber',
  descriptionHash: 'string',
  publicationDate: 'datetime', // When the result signature will be public
  email: 'email' // (optional) for notification purposes
}
```
* oracleAddress: `string`.
> Ethereum address that will sign the result, must be in the wallet.

* config: `object`

# updateResult
`updateResult(resultObject, oracleAddress, config)`

Can only be done before result signature is published.

* resultObject: `object`.
```js
{
  result: 'bigNumber',
  descriptionHash: 'string',
  publicationDate: 'datetime', // When the result signature will be public
  email: 'email' // (optional) for notification purposes
}
```

# reportResult
`reportResult(report, descriptionHash, oracleAddress, signerAddress, config)`

Sends to the oracle an email notifying of possible errors in the event resolution. Only if result signature is not published and the oracle posted the result with an email.

* report: `string`
> Message explaining the reason of the report

* descriptionHash: `string`
> identifies the event description

* oracleAddress: `string`
> Ethereum address of the oracle we want to notify

* signerAddress: `string`
> Our Ethereum address we will use to sign the report message

# getEvents
`getEvents(config, filters)`

Get events from REST API with given filters

* config: `object`
* filters: `object` (optional)
> * creator_address: `string`, ethereum address of the description creator.
> * oracle_addresses: `string`, ethereum addresses comma separated of off-chain-oracles.
> * resolution_date_gt: `dateTime` [ISO 8641](https://en.wikipedia.org/wiki/ISO_8601)
> * description_hashes: `string`, description hashes comma separated.
> * include_whitelisted_oracles: `True|true|1`, includes whitelisted oracle's events.
> * page: `integer`
> * page_size: `integer`

# createEventRevision
`createEventRevision(revision, oracleAddress, config)`

* revision: `object`
```js
const discreteRevision = {
  title: 'string',
  description: 'string',
  sourceURL: 'url',
  resolutionDate: 'datetime',
  outcomes: ['string'],  
  nonce: 'integer', // Incremental index, 0 for first revision
  descriptionHash: 'string'
}

const rangedRevision = {
  title: 'string',
  description: 'string',
  sourceURL: 'url',
  resolutionDate: 'datetime',
  unit: 'string',
  decimals: 'integer',
  nonce: 'integer', // Incremental index, 0 for first revision
  descriptionHash: 'string'
}
```

* oracleAddress: `string`
> Ethereum address that signs the revision

* config: `object`

# getContracts
`getContracts(filters, config)`

Gets accounts and contracts addresses from API.

* filters: `object`
> * oracle_addresses: Creator of contract
> * include_whiteslited_contracts: Includes whitelisted contracts

* config: `object`

# getOracleDetails
`getOracleDetails(config, address)`

* config: `object`
* address: `string`
> Oracle Ethereum address


# addOffChainOracle
`addOffChainOracle(oracle, oracleAddress, config)`

* oracle: `object`
```js
{
  name: 'string'
}
```
* oracleAddress: `string`
> Ethereum address

* config: `object`
