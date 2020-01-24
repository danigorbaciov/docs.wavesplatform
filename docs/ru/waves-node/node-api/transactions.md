# Транзакции

## GET /transactions/info/{id}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает данные транзакции по ID.

**Параметры запроса:**

```
"id" - Transaction ID
```

**Пример ответа в JSON:**

```js
{
  "type": 4,
  "id": "52GG9U2e6foYRKp5vAzsTQ86aDAABfRJ7synz7ohBp19",
  "sender": "3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",
  "senderPublicKey": "CRxqEuxhdZBEHX42MU4FfyJxuHmbDBTaHMhM3Uki7pLw",
  "recipient": "3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",
  "assetId": "E9yZC4cVhCDfbjFJCc9CqkAtkoFy5KaCe64iaxHM2adG",
  "amount": 100000,
  "feeAsset": null,
  "fee": 100000,
  "timestamp": 1479313236091,
  "attachment": "string",
  "signature": "GknccUA79dBcwWgKjqB7vYHcnsj7caYETfncJhRkkaetbQon7DxbpMmvK9LYqUkirJp17geBJCRTNkHEoAjtsUm",
  "height": 7782
}
```

## GET /transactions/address/{address}/limit/{limit}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает заданное количество последних странзакций по адресу аккаунта.

**Параметры запроса:**

```
"address" - Адрес аккаунта в Base58
"limit" - Количество возвращаемых транзакций, max = 50.
```

**Пример ответа в JSON:**

```js
[
  [
    {
      "type": 2,
      "id": "4XE4M9eSoVWVdHwDYXqZsXhEc4q8PH9mDMUBegCSBBVHJyP2Yb1ZoGi59c1Qzq2TowLmymLNkFQjWp95CdddnyBW",
      "fee": 100000,
      "timestamp": 1479313097422,
      "signature": "4XE4M9eSoVWVdHwDYXqZsXhEc4q8PH9mDMUBegCSBBVHJyP2Yb1ZoGi59c1Qzq2TowLmymLNkFQjWp95CdddnyBW",
      "sender": "3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",
      "senderPublicKey": "CRxqEuxhdZBEHX42MU4FfyJxuHmbDBTaHMhM3Uki7pLw",
      "recipient": "3N9iRMou3pgmyPbFZn5QZQvBTQBkL2fR6R1",
      "amount": 1000000000
    }
  ]
]
```

## GET /transactions/unconfirmed

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает список неподтверждённых транзакций пула ноды.

**Пример ответа в JSON:**

```js
[
  {
    "type": 4,
    "id": "52GG9U2e6foYRKp5vAzsTQ86aDAABfRJ7synz7ohBp19",
    "sender": "3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",
    "senderPublicKey": "CRxqEuxhdZBEHX42MU4FfyJxuHmbDBTaHMhM3Uki7pLw",
    "recipient": "3NBVqYXrapgJP9atQccdBPAgJPwHDKkh6A8",
    "assetId": "E9yZC4cVhCDfbjFJCc9CqkAtkoFy5KaCe64iaxHM2adG",
    "amount": 100000,
    "feeAsset": null,
    "fee": 100000,
    "timestamp": 1479313236091,
    "attachment": "string",
    "signature": "GknccUA79dBcwWgKjqB7vYHcnsj7caYETfncJhRkkaetbQon7DxbpMmvK9LYqUkirJp17geBJCRTNkHEoAjtsUm"
  }
]
```

## GET /transactions/unconfirmed/size

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает количество неподтвержденных транзакций в UTX пуле.

**Пример ответа в JSON:**

```js
{
  "size": 3
}
```

## GET /transactions/unconfirmed/info/{id}
![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает неподтвержденную транзакцию по ID.

**Параметры запроса:**

```
"id" - Transaction ID
```

**Пример ответа в JSON:**

```js
{
  "type": 4,
  "id": "F4SPn6SNHiQB6DCATrVMqsM3s4RKTPVq8c7uPZEJ8YRN",
  "sender": "3PBST44zh2rDhxXW97AEkYYtufFLtf2CuWP",
  "senderPublicKey": "4NQqZba92s8NpQBMQhcb53d5oVpn9fWR2VEX5uhDHZiD",
  "fee": 100000,
  "timestamp": 1548847534028,
  "signature": "28cq23pr8YezgqrwSuHKTTqUuSDJPBdfC9ACQQ15jAzxYZXowfmJFfcXmHsC5L1uUmBLPZySLCY4X4tsmetsLEx2",
  "proofs": [
    "28cq23pr8YezgqrwSuHKTTqUuSDJPBdfC9ACQQ15jAzxYZXowfmJFfcXmHsC5L1uUmBLPZySLCY4X4tsmetsLEx2"
  ],
  "version": 1,
  "recipient": "3P7wD8Un2FpT8XC3p5ADgiRJEyeycWxs2Tj",
  "assetId": "C9XD25wtUf4MTqbyDX8zqxpY2aXk6recZd5Bwtq7CUJS",
  "feeAssetId": null,
  "feeAsset": null,
  "amount": 1000000000000,
  "attachment": ""
}
```

или

```js
{
  "status": "error",
  "details": "Transaction is not in UTX"
}
```

## POST /transactions/calculateFee

![master](https://img.shields.io/badge/node-&gt;%3D0.14.3-4bc51d.svg)

Считает и возвращает комиссию произвольной транзакции. Тип транзакции может быть задан в теле запроса. Бывают следующие типы:

| Код | Тип транзакции |
| :--- | :--- |
| 3 | Issue |
| 4 | Transfer |
| 5 | Reissue |
| 6 | Burn |
| 8 | Lease |
| 9 | Lease Cancel |
| 10 | Alias |
| 11 | Mass Transfer |
| 12 | Data |
| 13 | Set Script |
| 14 | Sponsorship |

**Параметры запроса:**

```
"type" - тип транзакции
"senderPublicKey" - публичный ключ отправителя
"sender" игнорируется
"fee" игнорируется
и все прочие параметры подходящие для транзакции выбранного типа.
```

**Пример ответа в JSON:**

```js
{
 "type": 10,
 "timestamp": 1516171819000,
 "sender": "3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
 "alias": "ALIAS",
}
```

или

```js
{
  "type": 4,
  "sender": "3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
  "recipient": "3P8JYPHrnXSfsWP1LVXySdzU1P83FE1ssDa",
  "amount": 1317209272,
  "feeAssetId": "8LQW8f7P5d5PZM7GtZEBgaqRPGSzS3DfPuiXrURJ4AJS",
  "attachment": "string"
}
```

**Пример ответа в JSON:**

```
{
  "feeAssetId": null,
  "feeAmount": 10000
}
```

or

```js
{
  "feeAssetId": "8LQW8f7P5d5PZM7GtZEBgaqRPGSzS3DfPuiXrURJ4AJS",
  "feeAmount": 10000
}
```

## POST /transactions/sign

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Подписывает произвольную транзакцию. Требует API ключ, а также необходимо задать тип транзакции в теле запроса. Бывают слебующие типы:

| Код | Тип транзакции |
| :--- | :--- |
| 3 | Issue |
| 4 | Transfer |
| 5 | Reissue |
| 6 | Burn |
| 8 | Lease |
| 9 | Lease Cancel |
| 10 | Alias |
| 11 | Mass Transfer |
| 12 | Data |
| 13 | Set Script |
| 14 | Sponsorship |

Опциональный параметр `timestamp` может быть задан, чтобы отображать отметку времени в миллисекундах. Если параметр не исключен, то используется метное время сервера.

**Параметры запроса:**

```
"type" - тип транзакции
"timestamp" - [Опциональный параметр] отметка времени в миллисекундах
и все прочие параметры подходящие для транзакции выбранного типа.
```

**Пример запроса в JSON**

```js
{
 "type": 10,
 "timestamp": 1516171819000,
 "sender": "3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
 "fee": 100000,
 "alias": "ALIAS",
}
```

или

```js
{
  "type": 4,
  "sender": "3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
  "recipient": "3P8JYPHrnXSfsWP1LVXySdzU1P83FE1ssDa",
  "amount": 1317209272,
  "fee": 100000,
  "attachment": "string"
}
```

**Пример ответа в JSON**

```js
{
 "type":10,
 "id":"9q7X84wFuVvKqRdDQeWbtBmpsHt9SXFbvPPtUuKBVxxr",
 "sender":"3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
 "senderPublicKey":"G6h72icCSjdW2A89QWDb37hyXJoYKq3XuCUJY2joS3EU",
 "fee":100000000,
 "timestamp":46305781705234713,
 "signature":"4gQyPXzJFEzMbsCd9u5n3B2WauEc4172ssyrXCL882oNa8NfNihnpKianHXrHWnZs1RzDLbQ9rcRYnSqxKWfEPJG",
 "alias":"dajzmj6gfuzmbfnhamsbuxivc"
}
```

## POST /transactions/sign/{signerAddress}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Подписывает произвольную транзакцию приватным ключом сайнера. Требует API ключ, адрес сайнера, а также необходимо задать тип транзакции в теле запроса.

`signerAddress` должен быть создан в [POST /addresses](https://docs.wavesplatform.com/development-and-api/node-api/address.html#post-addresses).

Бывают слебующие типы:

| Код | Тип транзакции |
| :--- | :--- |
| 3 | Issue |
| 4 | Transfer |
| 5 | Reissue |
| 6 | Burn |
| 8 | Lease |
| 9 | Lease Cancel |
| 10 | Alias |
| 11 | Mass Transfer |
| 12 | Data |
| 13 | Set Script |
| 14 | Sponsorship |

Можно дополнительно задать параметр `timestamp`, который представляет временную метку транзакции в миллисекундах. Если параметр исключен, то используется метное время сервера.

**Параметры запроса:**

```
"type" - Тип транзакции
"timestamp" - [Опциональный параметр] отметка времени в миллисекундах
и все прочие параметры подходящие для транзакции выбранного типа.
```

**Пример запроса в JSON:**

```js
{
 "type": 10,
 "timestamp": 1516171819000,
 "sender": "3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
 "fee": 100000,
 "alias": "ALIAS",
}
```

**Пример ответа в JSON:**

```js
{
 "type":10,
 "id":"9q7X84wFuVvKqRdDQeWbtBmpsHt9SXFbvPPtUuKBVxxr",
 "sender":"3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
 "senderPublicKey":"G6h72icCSjdW2A89QWDb37hyXJoYKq3XuCUJY2joS3EU",
 "fee":100000000,
 "timestamp":46305781705234713,
 "signature":"4gQyPXzJFEzMbsCd9u5n3B2WauEc4172ssyrXCL882oNa8NfNihnpKianHXrHWnZs1RzDLbQ9rcRYnSqxKWfEPJG",
 "alias":"dajzmj6gfuzmbfnhamsbuxivc"
}
```

## POST /transactions/broadcast

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Передает подписанную транзакцию любого типа.

**Параметры запроса:**

```
"type" - Тип транзакции
и все прочие параметры подходящие для транзакции выбранного типа.
```

**Пример запроса в JSON:**

```js
{
 "type":10,
 "senderPublicKey":"G6h72icCSjdW2A89QWDb37hyXJoYKq3XuCUJY2joS3EU",
 "fee":100000000,
 "timestamp":46305781705234713,
 "signature":"4gQyPXzJFEzMbsCd9u5n3B2WauEc4172ssyrXCL882oNa8NfNihnpKianHXrHWnZs1RzDLbQ9rcRYnSqxKWfEPJG",
 "alias":"dajzmj6gfuzmbfnhamsbuxivc"
}
```

**Пример ответа в JSON:**

```js
{
 "type":10,
 "id":"9q7X84wFuVvKqRdDQeWbtBmpsHt9SXFbvPPtUuKBVxxr",
 "sender":"3MtrNP7AkTRuBhX4CBti6iT21pQpEnmHtyw",
 "senderPublicKey":"G6h72icCSjdW2A89QWDb37hyXJoYKq3XuCUJY2joS3EU",
 "fee":100000000,
 "timestamp":46305781705234713,
 "signature":"4gQyPXzJFEzMbsCd9u5n3B2WauEc4172ssyrXCL882oNa8NfNihnpKianHXrHWnZs1RzDLbQ9rcRYnSqxKWfEPJG",
 "alias":"dajzmj6gfuzmbfnhamsbuxivc"
}
```

<a id="post-tx-status"></a>

## POST /transactions/status

![master](https://img.shields.io/badge/node-%3E%3D%201.1.7-brightgreen)

Возвращает список статусов странзакций по ID транзакций. В полученном списке сохраняется такой же порядок ID транзакций, как в запросе. Если ID транзакций не были заданы, запрос будет возвращём с ошибкой.

**Параметры запроса:**

`id` - transaction id

**Пример запроса в JSON:**

```js
[
  {
    "id": "H27nMqvLp514M9fFoKbn4qCvFtG3VGzMGcN7noDyDv6C"
  },
  {
    "id": "Bi2vXQdUTsUPRDLE4tWkCFNVNkLjRtvy9PuvWd5iNP63"
  },
  {
    "id": "Ew2mxDagrDJevuaXKUuA48e8QD5evkDr5Zpv7ERVpCN2"
  }
]
```

**Пример ответа в JSON:**

- `id` - transaction ID
- `status` - transaction status. `not_found` - transaction not found, `unconfirmed` - transaction is in UTX-pool, `confirmed` - transaction is in the block or microblock.
- `confirmations` - current blockchain height minus height of block the transaction was included in.
- `height` - transaction's height in the blockchain.

```js
[
  {
    "id": "H27nMqvLp514M9fFoKbn4qCvFtG3VGzMGcN7noDyDv6C",
    "status": "confirmed",
    "confirmations": 120,
    "height": 1772853
  },
  {
    "id": "Bi2vXQdUTsUPRDLE4tWkCFNVNkLjRtvy9PuvWd5iNP63",
    "status": "not_found"
  },
  {
    "id": "Ew2mxDagrDJevuaXKUuA48e8QD5evkDr5Zpv7ERVpCN2",
    "status": "unconfirmed"
  }
]
```

<a id="get-tx-status"></a>

## GET /transactions/status?id=tx1id&id=tx2id

![master](https://img.shields.io/badge/node-%3E%3D%201.1.7-brightgreen)

Возвращает список статусов странзакций по ID транзакций. В полученном списке сохраняется такой же порядок ID транзакций, как в запросе. Если ID транзакций не были заданы, запрос будет возвращём с ошибкой.

**Пример ответа в JSON:**

- `id` - transaction ID
- `status` - transaction status. `not_found` - transaction not found, `unconfirmed` - transaction is in UTX-pool, `confirmed` - transaction is in the block or microblock.
- `confirmations` - current blockchain height minus height of block the transaction was included in.
- `height` - transaction's height in the blockchain.

```js
[
  {
    "id": "H27nMqvLp514M9fFoKbn4qCvFtG3VGzMGcN7noDyDv6C",
    "status": "confirmed",
    "confirmations": 120,
    "height": 1772853
  },
  {
    "id": "Bi2vXQdUTsUPRDLE4tWkCFNVNkLjRtvy9PuvWd5iNP63",
    "status": "not_found"
  },
  {
    "id": "Ew2mxDagrDJevuaXKUuA48e8QD5evkDr5Zpv7ERVpCN2",
    "status": "unconfirmed"
  }
]
```
