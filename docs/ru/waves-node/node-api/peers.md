# Peers

## POST /peers/connect

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Подключение к пирам.

**Запрос:**

```js
{
	"host":"127.0.0.1",
	"port":"9084"
}
```

## GET /peers/connected
![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает список пиров, подключенных к ноде.

**Пример ответа в JSON:**

```js
{
  "peers": [
    {
      "address": "52.51.92.182/52.51.92.182:6863",
      "declaredAddress": "N/A",
      "peerName": "zx 182",
      "peerNonce": 183759
    },
    {
      "address": "ec2-52-28-66-217.eu-central-1.compute.amazonaws.com/52.28.66.217:6863",
      "declaredAddress": "N/A",
      "peerName": "zx 217",
      "peerNonce": 1021800
    }
  ]
}
```

## GET /peers/blacklisted

![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает список пиров в данный момент находящихся в черном списке ноды.

## GET /peers/all
![master](https://img.shields.io/badge/MAINNET-available-4bc51d.svg)

Возвращает список всех известных пиров не из черного списка с публично заявленными адресами.
