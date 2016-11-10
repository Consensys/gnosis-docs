# balanceOf
**Get balance of tokens for a given account/contract address. Returns request object.**
`balanceOf(tokenAddress, owner, config, callback)`

* tokenAddress: `string`
* owner: `string`
* config: `object`
* callback: `function`

# name
**Get token name. Returns request object.**
`name(tokenAddress, config, callback)`

* tokenAddress: `string`
* config: `object`
* callback: `function`

# symbol
**Get token symbol. Returns request object.**
`symbol(tokenAddress, config, callback)`

* tokenAddress: `string`
* config: `object`
* callback: `function`

# decimals
**Get token decimals. Returns request object.**
`name(tokenAddress, config, callback)`

* tokenAddress: `string`
* config: `object`
* callback: `function`

# allowance
**Get amount of tokens given address is allowed to spend. Returns request object.**
`allowance(tokenAddress, owner, spender, config, callback)`

* tokenAddress: `string`
* owner: `string`
* spender: `string`
* config: `object`
* callback: `function`

# approve
**Approves address to spend passed amount of tokens owned by sender. Returns a simulated transaction promise.**
`approve(tokenAddress, spender, value, config, callback)`

* tokenAddress: `string`
* spender: `string`
* value: `bigNumber`
* config: `object`
* callback: `function`

# totalSupply
**Get total amount of tokens available for token contract. Returns request object.**
`totalSupply(tokenAddress, config, callback)`

* tokenAddress: `string`
* config: `object`
* callback: `function`

# transfer
**Transfer to given address amount of tokens owned by sender. Returns a simulated transaction promise.**
`transfer(tokenAddress, addressTo, value, config, callback)`

* tokenAddress: `string`
* addressTo: `string`
* value: `bigNumber`
* config: `object`
* callback: `function`

# transferFrom
**Transfers from a third-party address given amount of token to another address. Returns simulated transaction promise.**
`transferFrom(tokenAddress, addressFrom, addressTo, value, config, callback)`

* tokenAddress: `string`
* addressFrom: `string`
* addressTo: `string`
* value: `bigNumber`
* config: `object`
* callback: `function`
