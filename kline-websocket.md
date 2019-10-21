## Websocket Connection
connect websocket with this url
```sh
wss://kline.indodax.com/ws
```
if you want to testing we recomended you can use [wscat](https://www.npmjs.com/package/wscat) 


## Supported Pairs
click [indodax api pairs here](https://www.npmjs.com/package/wscat) to see available pairs
*Important
use `id` params to put on the `$symbol`

## Intervals
| Periods ||
| ------ | ------ |
| 1m | 1 Minutes |
| 5m | 5 Minutes |
| 15m | 15 Minutes |
| 30m | 30 Minutes |
| 1h | 1 Hours |
| 1d | 1 Days |

## Kline
you can get trade data in from at 00:00 AM with format
`{"req":"$symbol.kline.$interval", "id":"Generated By Client"}` 
change $symbol with pair and $interval with periods. i.e below
#### Subscribe
```sh
#Request
{"sub":"btcidr.kline.1m", "id":"1"}

#Response
{
    "ch":"btcidr.1m",
    "ts":1570086780,
    "tick": {
        "pair":"btcidr",
        "type":"1m",
        "c":145300000,
        "h":145300000,
        "l":143900000,
        "o":145300000,
        "t":1566468720,
        "v":421514329
    }
}
```

#### Unsubscribe
```sh
#Request
{"unsub":"btcidr.kline.1m", "id":"1"}

#Response
{
    "id":"1",
    "status":"ok",
    "ts":1570088533,
    "unsubbed":"btcidr.kline.1m"
}
```

#### Request
```sh
#Request
{"req":"btcidr.kline.1m"}
#it will automaticly get data data start from 00:00 AM pertoday

{"req":"btcidr.kline.1m", "from":1569607200, "to":1569842641}
#it will get data data start from 1569607200 to 1569842641 in unixtime

#Response
{
    "rep":"btcidr.kline.1m",
    "status":"ok",
    "tick":[
        {
            "c":145012000,
            "h":145012000,
            "l":145012000,
            "o":145012000,
            "pair":"btcidr",
            "t":1566406800,
            "type":"1m",
            "v":401148449
        },
        {
            "c":145012000,
            "h":145012000,
            "l":145012000,
            "o":145012000,
            "pair":"btcidr",
            "t":1566406860,
            "type":"1m",
            "v":401148449
        }
    ]
}
```

## Trade Detail
you can get trade data in from at 00:00 AM with format
`{"req":"$symbol.trade"}` change symbol with pair. i.e below

#### Subscribe
```sh
#Request
{"sub":"btcidr.trade", "id":"id3"}
 
#Response
{
    "ch":"btcidr.trade",
    "ts":1570088960,
    "data":{
        "amount":32236,
        "direction":1, //buy
        "price":118876000,
        "trade_time":1570088960
    }
}
```

#### Unsubscribe
```sh
#Request
{"unsub":"btcidr.trade", "id":"id3"}
 
#Response
{
    "id":"id3",
    "status":"ok",
    "ts":1570091275,
    "unsubbed":"btcidr.trade"
}
```

#### Request
```sh
#Request
{"req":"btcidr.trade"}
#it will automaticly get data data start from 00:00 AM pertoday

{"req":"btcidr.trade", "from":1569607200, "to":1569842641}
#it will get data data start from 1569607200 to 1569842641 in unixtime

#Response
{
    "rep":"btcidr.trade",
    "status":"ok",
    "trade":[
        {
            "amount":900000,
            "direction":2, #Sell
            "price":118079000,
            "trade_time":1570035698
        },
        {
            "amount":1164359,
            "direction":1, #Buy
            "price":118080000,
            "trade_time":1570035965
        }
    ]
}
```