# CoinmarketcapFree

Cryptocurrency information from the Coinmarketcap site without a key.

## Installation

Install the gem and add to the application's Gemfile by executing:

    $ bundle add coinmarketcap_free

If bundler is not being used to manage dependencies, install the gem by executing:

    $ gem install coinmarketcap_free

## Usage
``` Ruby
list = CoinmarketcapFree::Cryptocurrencies.new(100, 1)
list.update
list.data
```

Result:
``` JSON
{
    "data": {
        "cryptoCurrencyList": [...],
        "totalCount": "8857"
        },
    "status": {...}
}
```

### If you want to sort in ascending, just write parameter:

``` Ruby
list = CoinmarketcapFree::Cryptocurrencies.new(100, 1, sort_type:'asc')
```
or
``` Ruby
list = CoinmarketcapFree::Cryptocurrencies.new(100, 1)
list.sort_type = 'asc'
```

Also other parameters for Cryptocurrencies:

* ```sort_by:``` String. Default: "market_cap". ("rank", "name", "symbol", "date_added", "market_cap", "market_cap_strict", "price", "circulating_supply", "total_supply", "max_supply", "num_market_pairs", "volume_24h", "percent_change_1h", "percent_change_24h", "percent_change_7d", "market_cap_by_total_supply_strict", "volume_7d", "volume_30d"). What field to sort the list of cryptocurrencies by.
* ```sort_type:``` String. Default: "desc". ("asc" or "desc"). The direction in which to order cryptocurrencies against the specified sort.
* ```convert:``` String. Default: 'USD'. Select cryptocurrencies to exchange. For example, many 'USD,BTC,ETH' to convert or only one 'USD'
* ```crypto_type:``` String. Default: "all". ("all", "coins", "tokens"). The type of cryptocurrency to include.
* ```tag_type:``` String. Default: "all". ("all", "defi", "filesharing"). The tag of cryptocurrency to include.
* ```audited:``` Boolean. false or true
* ```aux:``` String. Optionally specify a comma-separated list of supplemental data fields to return. Pass 'ath, atl, high24h, low24h, num_market_pairs, cmc_rank, date_added, max_supply, circulating_supply, total_supply, volume_7d, volume_30d, self_reported_circulating_supply, self_reported_market_cap' to include all auxiliary fields.
* ```tags:``` String. Usually choose 'mineable'.
* ```volume_24h_range:``` String. Optionally specify a threshold 24 hour USD volume to filter results by. For example, For example, '0~100000000000000000'
* ```percent_change_24h_range:``` String. Optionally specify a threshold 24 hour percent change to filter results by. For example, '0~100' or '-10~100'
* ```circulating_supply_range:``` String. Optionally specify a threshold circulating supply to filter results by. For example, '0~100000000000000000'
* ```price_range:``` String. Optionally specify a threshold USD price to filter results by. For example, '0~100000000000000000'
* ```market_cap_range:``` String. Optionally specify a threshold market cap to filter results by. For example, '0~100000000000000000'

### Returns an interval of historic market quotes:

``` Ruby
coin = CoinmarketcapFree::Coin.new(1, '1D')
coin.update
coin.data
```

Result:
``` JSON
 {
     "data": {
         "points": {
             "1673192010": {
               "v": [
                     16953.771282696678,
                     7609543976.45,
                     326457581376.786557398500,
                     1,
                     19255750.00000000000000000000
                 ],
                 "c": [
                     16953.771282696678,
                     7609543976.45,
                     326457581376.786557398500
                 ]
             },
           ...
         }
     },
     "status": {
         "timestamp": "2023-01-08T15:33:30.271Z",
         "error_code": "0",
         "error_message": "SUCCESS",
         "elapsed": "2",
         "credit_count": 0
     }
 }
 
```

Parameters for Coin:

* ```id``` Integer. Cryptocurrency identifier from coinmarketcap. For example, Bitcoin has the number 1
* ```range_time``` String. Range time. For example, '1D', '7D', '1M', '3M', '1Y', 'YTD', 'ALL' or custom range '1668981600~1671659999'

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and the created tag, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/cosmic-1/coinmarketcap_free.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
