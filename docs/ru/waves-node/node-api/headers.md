# Request headers

## api-key

[API ключ](https://en.wikipedia.org/wiki/Application_programming_interface_key) владельца ноды очень важен как и seed фраза и пароль кошелька.

API ключ передается в HTTP хэдере как незащищенный plain текст в `api-key`. Злоумышленник может перехватить его во время передачи по сети и использовать его для перевода ваших активов на любой адрес! Очень важно защищать передачу с помощью HTTPS или SSH ретрансляции порта.

Имейте ввиду, что нода не имеет встроенной поддержки HTTPS. Рассмотрите возможность применения HTTPS-proxy, например, nginx.

## large-significand-format=string

Устанавливает формат сериализации для денежных полей. Если установлено, поле будет сериализовано в JSON как строка, в противном случае - как число. Это может быть полезно для значений с длинной дробной частью логарифма.

### Пример

```
curl -X GET --header 'Accept: application/json; large-significand-format=string' 'https://nodes.wavesnodes.com/blocks/headers/last'

```

Ниже приведен список конечных точек, принимающих этот хэдер.

#### GET /addresses/balance/{address}/{confirmations}

Affected field: `balance`.

#### GET /addresses/balance/details/{address}

Affected fields: `regular`, `generating`, `available`, `effective`.

#### GET /addresses/effectiveBalance/{address}/{confirmations}

Affected field: `balance`.

#### GET /addresses/effectiveBalance/{address}

Affected field: `balance`.

#### GET /addresses/balance/{address}

Affected field: `balance`.

#### GET /blocks/headers/last

Affected field: `reward`, `totalFee`.

#### GET /blocks/headers/at/{height}

Affected fields: `reward`, `totalFee`.

#### GET /blocks/headers/seq/{from}/{to}

Affected fields: `reward`, `totalFee`.

#### GET /blocks/at/{height}

Affected fields: `reward`, `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`, `totalFee`.

#### GET /blocks/signature/{signature}

Affected fields: `reward`, `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`, `totalFee`.

#### GET /blocks/address/{address}/{from}/{to}

Affected fields: `reward`, `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`, `totalFee`.

#### GET /blocks/last

Affected fields: `reward`, `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`, `totalFee`.

#### GET /blocks/seq/{from}/{to}

Affected fields: `reward`, `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`, `totalFee`.

#### GET /blockchain/rewards/{height}

Affected fields: `totalWavesAmount`, `currentReward`, `minIncrement`.

#### GET /blockchain/rewards

Affected fields: `totalWavesAmount`, `currentReward`, `minIncrement`.

#### POST /transactions/calculateFee

Affected field: `feeAmount`.

#### GET /transactions/info/{id}

Affected fields: `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`.

#### GET /transactions/unconfirmed/info/{id}

Affected fields: `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`.

#### GET /transactions/address/{address}/limit/{limit}

Affected fields: `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`.

#### POST /transactions/broadcast

Affected fields: `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`.

#### GET /transactions/unconfirmed

Affected fields: `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`.

#### GET /assets/balance/{address}

Affected fields: `balance`, `minSponsoredAssetFee`, `sponsorBalance`, `quantity`, `fee`

#### GET /assets/nft/{address}/limit/{limit}

Affected fields: `balance`, `minSponsoredAssetFee`, `sponsorBalance`, `quantity`, `fee`

#### GET /assets/{assetId}/distribution/{height}/limit/{limit}

Affected field: asset ID.

#### GET /assets/details/{assetId}

Affected field: `quantity`.

#### GET /assets/balance/{address}/{assetId}

Affected field: `balance`.

#### GET /consensus/generatingbalance/{address}

Affected field: `balance`.

#### GET /debug/balances/history/{address}

Affected field: `balance`.

#### GET /debug/stateChanges/info/{id}

Affected field: `fee`.

#### GET /debug/stateChanges/address/{address}/limit/{limit}

Affected fields: `fee`, `amount`, `sellMatcherFee`, `price`, `matcherFee`, `buyMatcherFee`, `totalAmount`.

#### GET /debug/portfolios/{address}

Affected fields: `balance`, `in`, `out`.
