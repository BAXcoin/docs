API Module <a name="docs_home"></a>
===================================

### API Functions & Variables

The API Module features the following functions:

* [`$.fn.blockstrap.api.address`(hash, currency, callback, service, return_raw)](#api_address)
* [`$.fn.blockstrap.api.addresses`(hashes, currency, callback, service)](#api_addresses)
* [`$.fn.blockstrap.api.balance`(hash, currency, callback, service)](#api_balance)
* [`$.fn.blockstrap.api.block`(height, currency, callback, service, return_raw)](#api_block)
* [`$.fn.blockstrap.api.map`(currency)](#api_map)
* [`$.fn.blockstrap.api.market`(currency, stat, callback, service, return_raw)](#api_market)
* [`$.fn.blockstrap.api.request`(url, callback, type, data, currency, call, username, password)](#api_request)
* [`$.fn.blockstrap.api.relay`(hash, currency, callback, service, return_raw)](#api_relay)
* [`$.fn.blockstrap.api.results`(defaults, results, currency, request, callback)](#api_results)
* [`$.fn.blockstrap.api.transaction`(txid, currency, callback, service, return_raw)](#api_transaction)
* [`$.fn.blockstrap.api.transactions`(address, currency, callback, service, return_raw)](#api_transactions)
* [`$.fn.blockstrap.api.unspents`(address, currency, callback, confirms, service, return_raw)](#api_unspents)
* [`$.fn.blockstrap.api.url`(action, key, currency)](#api_url)

You may also want to learn about [API Mapping](#api_mapping).

--------------------------------------------------------------------------------

#### `api.address`(hash, currency, callback, service, return_raw) <a name="api_address" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to get information pertaining to an address.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    address: 'N/A',
    hash: 'N/A',
    tx_count: 0,
    currency: currency,
    received: 0,
    balance: 0
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.address('1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk', 'btc', function(results)
{
    // Your callback
    console.log(results)
});
```

Which should provide the following results:

<!--pre-javascript-->
```
{
    address: "1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk",
    balance: 0,
    currency: "btc",
    hash: "0030ececbad05ffcdff89f3f26e38ca3d735a8de",
    received: 5000000000,
    tx_count: 2
}
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.addresses`(hashes, currency, callback, service) <a name="api_addresses" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to get information pertaining to multiple addresses.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    address: 'N/A',
    hash: 'N/A',
    tx_count: 0,
    currency: currency,
    received: 0,
    balance: 0
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.addresses(
    ['1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk, 12higDjoCCNXSA95xZMWUdPvXNmkAduhWv'], 
    'btc', function(results)
    {
        // Your callback
        console.log(results)
    }
);
```

Which should provide the following results:

<!--pre-javascript-->
```
{
    address: "1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk",
    balance: 0,
    currency: "btc",
    hash: "0030ececbad05ffcdff89f3f26e38ca3d735a8de",
    received: 5000000000,
    tx_count: 2
},
{
    address: "12higDjoCCNXSA95xZMWUdPvXNmkAduhWv",
    balance: 0,
    currency: "btc",
    hash: "12ab8dc588ca9d5787dde7eb29569da63c3a238c",
    received: 7762439255612,
    tx_count: 75
}
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.balance`(hash, currency, callback, service) <a name="api_balance" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to get the balance of an address.

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.balance('1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk', 'btc', function(results)
{
    // Your callback
    console.log(results)
});
```

Which should provide the results as an integer.

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.block`(height, currency, callback, service, return_raw) <a name="api_block" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to get information pertaining to a block.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    currency: currency,
    height: 'N/A',
    hash: 'N/A',
    prev: 'N/A',
    tx_count: 0,
    time: 0
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.block('15968', 'btc', function(results)
{
    // Your callback
    console.log(results)
});
```

Which should provide the following results:

<!--pre-javascript-->
```
{
    currency: "btc",
    hash: "00000000201016a83272835468d457d15965d57f57c0da5944dc94ea9389f360",
    height: 15968,
    prev: "00000000abae6b44fa98526e865a08820f4528eda46cad40445de3690c502ae8",
    time: 1243609567,
    tx_count: 2
}
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.map`(currency) <a name="api_map" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function is used internally to share API end-points.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.market`(currency, stat, callback, service, return_raw) <a name="api_market" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function is used to return the current market conditions of the defined `currency`. By default it will return the entire object as follows:

<!--pre-javascript-->
```
{
    btc_to_usd: 0,
    daily_txs: 0,
    daily_sent: 0,
    hash_rate: 0,
    btc_discovered: 0,
    market_cap: 0
}
```

If a valid `stat` is defined, it will instead return the results of that stat.

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.request`(url, callback, type, data, currency, call, username, password) <a name="api_request" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function is used internally by other functions within this class to route requests and should not be directly used.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.relay`(hash, currency, callback, service, return_raw) <a name="api_relay" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to relay a raw transaction.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    currency: currency,
    txid: 'N/A'
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.relay('__RAW_TX__', 'btc', function(results)
{
    // Your callback
    console.log(results)
});
```

Which should provide the following results:

<!--pre-javascript-->
```
{
    currency: "btc",
    txid: "00000000201016a83272835468d457d15965d57f57c0da5944dc94ea9389f360"
}
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.results`(defaults, results, currency, request, callback) <a name="api_results" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function is used internally by other functions within this class to format requested results and should not be directly used.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.transaction`(txid, currency, callback, service, return_raw) <a name="api_transaction" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to get information pertaining to a transaction.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    url: '#',
    currency: currency,
    txid: 'N/A',
    size: 'N/A',
    block: 'N/A',
    time: 0,
    input: 0,
    output: 0,
    fees: 0
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.transaction(
    '06032a172f88ba823785f87341eab26ee7a2eb2de9d2f105220d6580e3affc16', 
    'btc', function(results)
    {
        // Your callback
        console.log(results)
    }
);
```

Which should provide the following results:

<!--pre-javascript-->
```
{
    block: 15968,
    currency: "btc",
    fees: 0,
    input: 300000000000,
    output: 300000000000,
    size: 6883,
    time: 1243609567,
    txid: "06032a172f88ba823785f87341eab26ee7a2eb2de9d2f105220d6580e3affc16",
    url: "#transaction?txid=06032a172f88ba823785f87341eab26ee7a2eb2de9d2f105220d6580e3affc16"
}
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.transactions`(address, currency, callback, service, return_raw) <a name="api_transactions" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to get information pertaining to all the transactions of a single address.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    url: '#',
    currency: currency,
    txid: 'N/A',
    size: 'N/A',
    block: 'N/A',
    time: 0,
    input: 0,
    output: 0,
    fees: 0
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.transactions('1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk', 'btc', function(results)
{
    // Your callback
    console.log(results)
});
```

Which should provide the following results:

<!--pre-javascript-->
```
{
    block: 15968,
    currency: "btc",
    fees: 0,
    input: 300000000000,
    output: 300000000000,
    size: 6883,
    time: 1243609567,
    txid: "06032a172f88ba823785f87341eab26ee7a2eb2de9d2f105220d6580e3affc16",
    url: "#transaction?txid=06032a172f88ba823785f87341eab26ee7a2eb2de9d2f105220d6580e3affc16"
},
    block: 15169,
    currency: "btc",
    fees: 0,
    input: 0,
    output: 5000000000,
    size: 135,
    time: 1242853427,
    txid: "7f065b4a2a7f5393a5d1b74e8f340ac961d21bb7e8b77a59c9db580eeaf78d03",
    url: "#transaction?txid=7f065b4a2a7f5393a5d1b74e8f340ac961d21bb7e8b77a59c9db580eeaf78d03"
}
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.unspents`(address, currency, callback, confirms, service, return_raw) <a name="api_unspents" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function uses the selected API to check an address for unspent inputs.

The information it is able to map (with the corresponding defaults) includes:

<!--pre-javascript-->
```
{
    txid: 'N/A',
    index: 0,
    value: 0,
    script: 'N/A'
}
```

Example usage of this function could look like:

<!--pre-javascript-->
```
var api = $.fn.blockstrap.modules.api;
api.unspents('1121cQLqCsDsLPAkJW5ddTCREZ7Bp4ufrk', 'btc', function(results)
{
    // Your callback
    console.log(results)
});
```

The `service` variable allows you to override the default API service for individual calls by providing one listed in configuration.

If `return_raw` is set to true, the raw results will be returned through `callback` __instead__ of passing through `api.results`.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### `api.url`(action, key, currency) <a name="api_url" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

This function is used internally by other functions within this class to help construct URLs prior to API requests and should not be directly used.

<a href="#docs_home"><small>- back to top</small></a>

--------------------------------------------------------------------------------

#### API Mapping <a name="api_mapping" class="pull-right" href="#docs_home"><i class="glyphicon glyphicon-upload"></i>- back to top</a>

Blockstrap does not lock you in to a specific API provider. We provide functionality that allows you to map each and every API call we make to a specific API end-point of your choosing. For example, if you wanted to map our wallet to the [Hello Block](http://helloblock.io) API you would supply the following map:

<!--pre-javascript-->
```
{
    "currencies": {
        "btc": {
            "currency": "Bitcoin",
            "lib": "bitcoin",
            "apis": {
                "blockstrap": "http://api.blockstrap.com/v0/btc/", 
                "helloblock": "https://mainnet.helloblock.io/v1/"
            },
            "fee": 0.0001
        },
        "multi": {
            "priate": true,
            "apis": {
                "blockstrap": "http://api.blockstrap.com/v0/multi/"
            }
        }
    },
    "apis": {
        "btc": {
            "helloblock": {
                "functions": {
                    "to": {
                        "address": "addresses/",
                        "addresses": "addresses?addresses=",
                        "transaction": "transactions/",
                        "transactions": "addresses/$call/transactions?limit=100",
                        "block": "blocks/",
                        "relay": "transactions/",
                        "relay_param": "rawTxHex",
                        "unspents": "addresses/$call/unspents?limit=100"
                    },
                    "from": {
                        "address": {
                            "key": "address",
                            "address": "address",
                            "hash": "hash160",
                            "tx_count": "txsCount",
                            "received": "confirmedReceivedValue",
                            "balance": "balance"
                        },
                        "addresses": {
                            "key": "addresses",
                            "delimiter": "&addresses=",
                            "address": "address",
                            "hash": "hash160",
                            "tx_count": "txsCount",
                            "received": "confirmedReceivedValue",
                            "balance": "balance"
                        },
                        "transaction": {
                            "key": "transaction",
                            "txid": "txHash",
                            "size": "size",
                            "block": "blockHeight",
                            "time": "blockTime",
                            "input": "totalInputsValue",
                            "output": "totalOutputsValue",
                            "value": "estimatedTxValue",
                            "fees": "fees"
                        },
                        "transactions": {
                            "key": "transactions",
                            "txid": "txHash",
                            "size": "size",
                            "block": "blockHeight",
                            "time": "blockTime",
                            "input": "totalInputsValue",
                            "inputs": "inputs",
                            "output": "totalOutputsValue",
                            "outputs": "outputs",
                            "value": "estimatedTxValue",
                            "fees": "fees"
                        },
                        "block": {
                            "key": "block",
                            "height": "blockHeight",
                            "hash": "blockHash",
                            "prev": "prevBlockHash",
                            "tx_count": "txsCount",
                            "time": "blockTime"
                        },
                        "relay": {
                            "txid": "txHash",
                            "inner": "transaction"
                        },
                        "unspents": {
                            "key": "unspents",
                            "confirmations": "confirmations",
                            "txid": "txHash",
                            "index": "index",
                            "value": "value",
                            "script": "scriptPubKey"
                        }
                    }
                }
            }
        }
    }
}
```
<a href="#docs_home"><small>- back to top</small></a>

As you can see from line 14 above it is also possible to include currencies that can be used privately, and __DO NOT__ show up in drop-down selections.

Please note the we currently support the following APIs (from default configuration):

* [Blockchains.io](http://blockchains.io) (6 Chains): select __`blockstrap`__ as service choice
* [SoChain.io](http://chain.so) (6 Chains): select __`sochain`__ as service choice
* [Blockr.io](http://blockr.io) (4 Chains): select __`blockr`__ as service choice
* [HelloBlock.io](https://helloblock.io/) (BTC only): select __`helloblock`__ as service choice

---

1. Related Articles
2. [Back to Modules](../../modules/)
3. [Accounts](../accounts/)
4. [API](../api/)
5. [Buttons](../buttons/)
6. [Contacts](../contacts/)
7. [Currencies](../currencies/)
8. [Data](../data/)
9. [Filters](../filters/)
10. [Forms](../forms/)
11. [Security](../security/)
12. [Styles](../styles/)
13. [Templates](../templates/)
14. [Table of Contents](../../../)
