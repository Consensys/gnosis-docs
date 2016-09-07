# createEvent
`createEvent(event, oracleAddress, config)`

  * event: `object`
  > (Discrete or Ranged see [Event Description](/api_reference/eventDescription))

  * oracleAddress: `string`
  > Ethereum address used to sign the event description. You must own this address

  * config: `object`
  
------
```js
// Response
 {
   data: event
 }
```

# subscribeOracleToEvent
`subscribeOracleToEvent(givenFee, descriptionHash, oracleAddress, email, config)`

* givenFee: `bigNumber`.
> Fee oracle charges for resolving the event.

* descriptionHash: `string`
> DescriptionHash that identifies the event.

* email: `email`
> Email to notify oracle when event needs to be resolved.

* config: `object`
