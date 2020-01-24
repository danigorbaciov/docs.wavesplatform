# Утилиты

## POST /utils/hash/secure
![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Получить безопасный хэш заданного сообщения.

**Запрос:**

```
ridethewaves!

```

**Пример ответа в JSON:**

```js
{
  "message": "ridethewaves!",
  "hash": "H6nsiifwYKYEx6YzYD7woP1XCn72RVvx6tC1zjjLXqsu"
}

```

## POST /utils/hash/fast
![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Быстрый хэш заданного сообщения.

**Запрос:**

```
ridethewaves!

```

**Пример ответа в JSON:**

```js
{
  "message": "ridethewaves!",
  "hash": "DJ35ymschUFDmqCnDJewjcnVExVkWgX7mJDXhFy9X8oQ"
}

```

## GET /utils/seed/{length}

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Сгенерировать случайный seed заданной длины.

**Пример ответа в JSON:**

```js
{
  "seed": "3XcHLU6bYRax1c"
}
```

## GET /utils/seed
![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Сгенерировать случайный seed.

**Пример ответа в JSON:**

```js
{
  "seed": "2uwLAe7Rp7TuNiBTKsmTEJ5wxGqkBHjcyPq2tMXiWye7"
}

```

## POST /utils/script/compile

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg) ![master](https://img.shields.io/badge/node-&gt;%3D0.13.3-4bc51d.svg)

Компилирует человекочитаемый код в представление Base58 для ноды.

**Тело запроса:**
A code.

**Параметры ответа:**

```
"script" - Base58-encoded представление скомпилированного скрипта ноды
"complexity" - Как компилируется скрипт
"extraFee" - Дополнительная комиссия за все транзакции от аккаунта со скриптом, если этот майнер и есть эта нода
```

**Пример валидного запроса:**

```
let x = 1
(x + 1) == 2
```

**Ответ:**

```json
{
  "script": "3rbFDtbPwAvSp2vBvqGfGR9nRS1nBVnfuSCN3HxSZ7fVRpt3tuFG5JSmyTmvHPxYf34SocMRkRKFgzTtXXnnv7upRHXJzZrLSQo8tUW6yMtEiZ",
  "complexity": 11,
  "extraFee": 10001
}
```

**Пример не валидного запроса:**

```
x == 1
```

**Ответ:**

```json
{
  "error": "Typecheck failed: A definition of 'x' is not found"
}
```

## POST /utils/script/estimate

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg) ![master](https://img.shields.io/badge/node-&gt;%3D0.13.3-4bc51d.svg)

Estimates a human-readable code into a Base58 representation for Node.

**Запрос:**
A code.

**Параметры ответа:**

```
"script" - Base58-encoded representation of compiled script for Node (what did you send in the body)
"scriptText" - String representation of a script (not decompiled!)
"complexity" - How script is complicated
"extraFee" - An extra fee for all transactions going from an account with this script if the miner is this node
```

**Пример валидного запроса:**

```
3rbFDtbPwAvSp2vBvqGfGR9nRS1nBVnfuSCN3HxSZ7fVRpt3tuFG5JSmyTmvHPxYf34SocMRkRKFgzTtXXnnv7upRHXJzZrLSQo8tUW6yMtEiZ
```

**Ответ:**

```json
{
  "script": "3rbFDtbPwAvSp2vBvqGfGR9nRS1nBVnfuSCN3HxSZ7fVRpt3tuFG5JSmyTmvHPxYf34SocMRkRKFgzTtXXnnv7upRHXJzZrLSQo8tUW6yMtEiZ",
  "scriptText": "FUNCTION_CALL(FunctionHeader(==,List(LONG, LONG)),List(CONST_LONG(1), CONST_LONG(2)),BOOLEAN)",
  "complexity": 11,
  "extraFee": 10001
}
```

**Пример не валидного запроса:**

```
This is even not a Base58 string!
```

**Ответ:**

```json
{
  "error": "Unable to decode base58: assertion failed: Wrong char in Base58 string"
}
```
