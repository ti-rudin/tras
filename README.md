# binance-api-php
Binance API  Class and examples of how to use the API.


#### Install

```php
composer require baitercel/binance-api-php dev-master
```

#### Getting started
```php
<?php
require 'BinanceClass.php';
$api = new Binance("API_Key","Secret");
```

#### Get latest price of a symbol
```php
$ticker = $api->prices();
print_r($ticker); // List prices of all symbols
echo "Price of BNB: {$ticker['BNBBTC']} BTC.\n";
```

#### Get all of your positions, including estimated BTC value
```php
$balances = $api->balances($ticker);
print_r($balances);
echo "BTC owned: ".$balances['BTC']['available']."\n";
echo "ETH owned: ".$balances['ETH']['available']."\n";
echo "Estimated Value: ".$api->btc_value." BTC\n";
```

#### Get all bid/ask prices
```php
$bookPrices = $api->bookPrices();
print_r($bookPrices);
```

#### Place a LIMIT order
```php
$quantity = 1;
$price = 0.0005;
$order = $api->buy("BNBBTC", $quantity, $price);
```

```php
$quantity = 1;
$price = 0.0006;
$order = $api->sell("BNBBTC", $quantity, $price);
```

#### Place a MARKET order
```php
$order = $api->buy("BNBBTC", $quantity, 0, "MARKET");
```

```php
$order = $api->sell("BNBBTC", $quantity, 0, "MARKET");
```

#### Get Trade History
```php
$trades = $api->trades("BNBBTC");
print_r($trades);
```

#### Get Market Depth
```php
$depth = $api->depth("ETHBTC");
print_r($depth);
```

#### Get Open Orders
```php
$openorders = $api->openOrders("BNBBTC");
print_r($openorders);
```

#### Get Order Status
```php
$orderid = "7610385";
$orderstatus = $api->orderStatus("ETHBTC", $orderid);
print_r($orderstatus);
```

#### Cancel an Order
```php
$response = $api->cancel("ETHBTC", $orderid);
print_r($response);
```

#### Get all account orders; active, canceled, or filled.
```php
$orders = $api->orders("BNBBTC");
print_r($orders);
```

#### Get Kline/candlestick data for a symbol
```php
//Periods: 1m,3m,5m,15m,30m,1h,2h,4h,6h,8h,12h,1d,3d,1w,1M
$ticks = $api->candlesticks("BNBBTC", "5m");
print_r($ticks);
```
