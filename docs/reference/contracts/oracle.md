# isOutcomeSet
**Checks if event outcome has been set with challenge period over. Returns request object.**
`isOutcomeSet(resolverAddress, eventIdentifier, config, callback)`

* resolverAddress: `string`    
> oracle contract address    
* eventIdentifier: `string`
> event identifier in the oracle contract    
* config: `object`    
* callback: `function`    

# getOutcome
**Returns outcome if event has been resolved, raises an exception if not. Returns request object.**
`getOutcome(resolverAddress, eventIdentifier, config, callback)`   

* resolverAddress: `string`    
> oracle contract address    
* eventIdentifier: `string`
> event identifier in the oracle contract    
* config: `object`    
* callback: `function`    

# getOffChainFee
**Returns fee value in bigNumber for a given array of fee signatures.**
`getOffChainFee(descriptionHash, feeSignatures)`

* descriptionHash: `string|bigNumber`
* feeSignatures: `array of feeSignatures`
```js
[
  {
    message: 'bigNumber|string',
    v: 'bigNumber|string',
    r: 'bigNumber|string',
    s: 'bigNumber|string'
  }
]
```

# getEventData
**Get event data stored in oracle contract for a given event. Ultimate Oracle
event data is the array of Off-chain-oracles. Returns a request object**
`getEventData(resolverAddress, eventIdentifier, config, callback)`

* resolverAddress: `string`    
> oracle contract address    
* eventIdentifier: `string`
> event identifier in the oracle contract    
* config: `object`    
* callback: `function`    

# registerEvent
**Creates event in he oracle contract address. Returns simulated transaction promise.**
`registerEvent(resolverAddress, eventData, config, callback)`

* resolverAddress: `string`    
> oracle contract address    
* eventData: `array of bigNumber|array of string (64 hex characters)`
> oracle event data
* config: `object`    
* callback: `function`  
