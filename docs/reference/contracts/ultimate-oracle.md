# getOracleOutcomes
**Get posted oracle outcomes against Ultimate Oracle contract before challenge period is over. Returns request object**
`getOracleOutcomes(descriptionHashes, oracleAddresses, config, callback)`

* descriptionHashes: `array of string|array of bigNumber`
* oracleAddresses: `array of string|array of bigNumber`
* config: `object`
* callback: `function`

# challengeWinningOutcome
**Sends a challenge for a given event and outcome sending a challenge amount of ether. Returns a simulated transaction promise.**
`challengeWinningOutcome(descriptionHash, outcome, challengeAmount, config, callback)`

* descriptionHash: `string|bigNumber`
* outcome: `bigNumber`
* challengeAmount: `bigNumber`    
> Ether amount sending for challenge    
* config: `object`
* callback: `function`

# getShares
**Get oracle challenge shares for given outcome in ether. Returns request object.**
`getShares(forAddress, descriptionHashes, outcomes, config, callback)`

* forAddress: `string`
* descriptionHashes: `array of string|array of bigNumber`
* outcomes: `array of bigNumber`
* config: `object`
* callback: `function`

# setUltimateOutcome
**Set ultimate outcome when challenge period is over. Returns a simulated transaction promise.**
`setUltimateOutcome(descriptionHash, config, callback)`

* descriptionHash: `string|bigNumber`
* config: `object`
* callback: `function`

# voteForUltimateOutcome
**Votes for a winning outcome sending a challenge amount of ether. Returns a simulated transaction promise.**
`voteForUltimateOutcome(descriptionHash, outcome, voteValue, config, callback)`

* descriptionHash: `string|bigNumber`
* outcome: `bigNumber`
* voteValue: `bigNumber`
> amount of ether send to the contract. Must be higher than actual front running challenge.    
* config: `object`
* callback: `function`

# getUltimateOutcomes
**Get ultimate oracle challenge state with front running outcome, shares and closing timestamp. Retuns a request object.**
`getUltimateOutcomes(descriptionHashes, config, callback)`

* descriptionHashes: `array of string|array of bigNumber`
* config: `object`
* callback: `function`

# withdraw
**Withdraw user challenge shares to owner account. Returns a simulated transaction promise.**
`withdraw(descriptionHash, config, callback)`

* descriptionHashes: `string|bigNumber`
* config: `object`
* callback: `function`

# setOutcome
**Signs outcome result and publishes it in the Ultimate Oracle contract**
`setOutcome(eventIdentifier, descriptionHash, outcomeIndex, oracleAddress, config, callback)`

* eventIdentifier: `string|bigNumber`
* descriptionHash: `string|bigNumber`
* outcomeIndex: `bigNumber`
* oracleAddress: `string`
> account signing result, must be in the wallet.    
* config: `object`
* callback: `function`

# setOutcomeWithSignature
**Sends existing result signatures. Returns a simulated transaction promise.**
`setOutcomeWithSignature(eventIdentifier, signatures, config, callback)`

* eventIdentifier: `string|bigNumber`
* signatures: `array of signatures`
```js
[
  outcomeIndex: 'bigNumber',
  v: 'bigNumber',
  r: 'bigNumber',
  s: 'bigNumber'
]
```
* config: `object`
* callback: `function`
