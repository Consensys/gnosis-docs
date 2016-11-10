You have two main ways to retrieve event descriptions from API:

## api.getEvents
`api.getEvents(config, filters)`

* `config`: Config object explained in [instance](/getting-started/instance)
* `filters`: (optional) Object of filters
    * creator_address: `string`, ethereum address of the description creator.
    * oracle_addresses: `string`, ethereum addresses comma separated of off-chain-oracles.
    * resolution_date_gt: `dateTime` [ISO 8641](https://en.wikipedia.org/wiki/ISO_8601)
    * description_hashes: `string`, description hashes comma separated.
    * include_whitelisted_oracles: `True|true|1`, includes whitelisted oracle's events.
    * page: `integer`
    * page_size: `integer`
    * title: `string`, contained in the description title.
    * tags: `string`, list of description tags separated by commas.

```js
    gnosis.api.getEvents(
      config,
      {}
    )
    .then(
      function(response){
        // response.data
        // response.data.count is the number of elements retrieved
        // response.data.results is an array of event descriptions objects

      },
      function(error){
        // API error
      }
    )
```

## state.updateEventDescriptions
`state.updateEventDescriptions(config, filters)`

This function uses the [state](/getting-started/state), default filters
are declared at the [config](/getting-started/instance) as:
```js
const eventDescriptionFilters = {
  oracleAddresses: "0x65039084cc6f4773291a6ed7dcf5bc3a2e894ff3,0x5dcd834cf776f47f138943e3466440009a2f2b00",
  includeWhitelistedOracles: true,
  pageSize: 50,// number of events returned by API for each page
  page: 1,
  creatorAddress: "0x5dcd834cf776f47f138943e3466440009a2f2b00",
  descriptionHashes: null,
  title: null,
  tags: null
}
```
And are merged with the filters that we pass as second parameter.
```js
gnosis.state.updateEventDescriptions(
  config,
  eventDescriptionFilters
)
then(
  function(response),
  function(error)
);
```
