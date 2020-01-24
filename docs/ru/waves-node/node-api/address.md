# Address

## GET /addresses

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Получить список всех адресов аккаунта кошелька ноды.

**Ответ:**

```js
[
"3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",
"3Mx2afTZ2KbRrLNbytyzTtXukZvqEB8SkW7"
]
```

### GET /addresses/seq/{from}/{to}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Получить список всех адресов аккаунтов с индексами заданного диапазона в кошельке ноды.

**Ответ:**

```js
[
"3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",  
"3Mx2afTZ2KbRrLNbytyzTtXukZvqEB8SkW7"
]
```

## POST /addresses

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Сгенерировать новый адрес аккаунта в кошельке. Необходим API ключ.

**Request params:**

```
  "address" - Адрес аккаунта в Base58
```

**Пример ответа в JSON:**

```js
{

"address": "3Mx2afTZ2KbRrLNbytyzTtXukZvqEB8SkW7"

}
```

## GET /addresses/balance/details/{address}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Получить данные о балансе:

```
"address" - адрес аккаунта в Base58
"Regular" — количество Waves, которое у вас есть, включая переданные в лизинг;
"Available" — количество Waves, которое у вас есть, не включая переданные в лизинг;
"Effective" — количество Waves, которое у вас есть, включая переданные Вам в лизинг;
"Generating" — минимальный генеэффективныйза последние 1000 блоков;
```

**Пример ответа в JSON:**

```js
{
  "address": "3P2HNUd5VUPLMQkJmctTPEeeHumiPN2GkTb",
  "regular": 1498883844,
  "generating": 1066926675599895,
  "available": 1498883844,
  "effective": 1067913688974251
}
```

## GET /addresses/balance/{address} <a id="get-addressesbalance"></a>

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Получить баланс аккаунта в WAVES на {address}:

```
  "address" - адрес аккаунта в Base58
```

**Пример ответа в JSON:**

```js
{

  "address": "3N3keodUiS8WLEw9W4BKDNxgNdUpwSnpb3K",
  "confirmations": 0,
  "balance": 100945889661986

}
```

## GET /addresses/balance/{address}/{confirmations}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Получить баланс аккаунта в WAVES на {address} после {confirmations}:

```
  "address" - адрес акаунта в Base58
  "confirmations" - N количество подтверждний
```

**Пример ответа в JSON:**

```js
{

"address": "3N3keodUiS8WLEw9W4BKDNxgNdUpwSnpb3K",

"confirmations": 500,

"balance": 100945388397565

}
```

## GET /addresses/scriptInfo/{address}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg) ![master](https://img.shields.io/badge/node->%3D0.13.3-4bc51d.svg)

Получить данные скрипта по адресу.

```
  "address" - адрес аккаунта в Base58
  "script" - Base58 представление скомпилированного скрипта. Поле отсутствует если скрипт не назначен для адреса
  "scriptText" - Текстовое представление скрипта. Поле отсутствует если скрипт не назначен для адреса
  "complexity" - Сложность скрипта
  "extraFee" - Дополнительная комиссия за все транзакции отправленные с данного аккаунта если майнер это и есть эта нода
```

**Пример ответа в JSON:**

```js
{
  "address": "3N3keodUiS8WLEw9W4BKDNxgNdUpwSnpb3K",
  "script": "3rbFDtbPwAvSp2vBvqGfGR9nRS1nBVnfuSCN3HxSZ7fVRpt3tuFG5JSmyTmvHPxYf34SocMRkRKFgzTtXXnnv7upRHXJzZrLSQo8tUW6yMtEiZ",
  "scriptText": "ScriptV1(BLOCK(LET(x,CONST_LONG(1)),FUNCTION_CALL(FunctionHeader(==,List(LONG, LONG)),List(FUNCTION_CALL(FunctionHeader(+,List(LONG, LONG)),List(REF(x,LONG), CONST_LONG(1)),LONG), CONST_LONG(2)),BOOLEAN),BOOLEAN))",
  "complexity": 11,
  "extraFee": 10001
}
```
