# calcCostsBuying
**Calculates costs of buying number of shares for a given market.**   
`calcCostsBuying(marketHash, initialFunding, shareDistribution, outcomeIndex, numberOfShares, config,
  [marketMakerAddress], callback)`

* marketHash: `string`
* initialFunding: `bigNumber`    
> initial Funding of market   
* shareDistribution: `array of bigNumber`   
> array of shares balances   
* outcomeIndex: `bigNumber`   
> selected outcome for buying   
* numberOfShares: `bigNumber`   
> number of shares to buy   
* config: `object`
* marketMakerAddress: `string` (optional)
* callback: `function`

# calcCostsBuyingWithFees
**Calculates costs of buying number of shares for a given market including fees. Returns a Promise.**   
`calcCostsBuyingWithFees(marketHash, outcomeIndex, numberOfShares, config, [marketMakerAddress])`

* marketHash: `string`
* outcomeIndex: `bigNumber`   
> selected outcome for buying   
* numberOfShares: `bigNumber`   
> number of shares to buy   
* config: `object`
* marketMakerAddress: `string` (optional)

# calcEarningsSelling
**Calculates earnings of selling number of shares for a given market.**  
`calcEarningsSelling(marketHash, initialFunding, shareDistribution, outcome, numberOfShares, config,
  [marketMakerAddress], callback)`

  * marketHash: `string`
  * initialFunding: `bigNumber`    
  > initial Funding of market   
  * shareDistribution: `array of bigNumber`   
  > array of shares balances   
  * outcomeIndex: `bigNumber`   
  > selected outcome for selling   
  * numberOfShares: `bigNumber`   
  > number of shares to sell   
  * config: `object`
  * marketMakerAddress: `string` (optional)
  * callback: `function`

# calcEarningsSellingWithFees
**Calculates earnings of selling number of shares for a given market including fees. Returns a Promise.**    
`calcEarningsSellingWithFees(marketHash, outcomeIndex, numberOfShares, config, [marketMakerAddress])`   

* marketHash: `string`
* outcomeIndex: `bigNumber`   
> selected outcome for selling       
* numberOfShares: `bigNumber`   
> number of shares to sell   
* config: `object`
* marketMakerAddress: `string` (optional)
