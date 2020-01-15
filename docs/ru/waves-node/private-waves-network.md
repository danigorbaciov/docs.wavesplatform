# Приватный блокчейн Waves

Выполните шаги, описанные ниже, чтобы настроить собственный приватный блокчейн Waves.

## Шаг 1

Установите Git, [Java 8](https://java.com/en/download/) и [sbt](http://www.scala-sbt.org/).

## Шаг 2

Клонируйте [репозиторий Waves](https://github.com/wavesplatform/Waves/).

## Шаг 3

Отредактируйте файл `node/src/test/resources/genesis.example.conf` с параметрами генезис блока.

**Пример**:

```bash
genesis-generator
{
  network-type: "L"  #байт идентификатор вашей приватной сети
  initial-balance: 10000000000000000  #первоначальный баланс в wavelets
  base-target: 153722867  #первоначальный параметр сложности
  average-block-delay: 60s #средняя задержка блока
  timestamp: 1500635421931 #закомментируйте этот параметр, чтобы использовать текущее время

  # сумма долей должна быть = initial-balance
  distributions
  {
    foo0 { # имя этого аккаунта. Отобразится при выводе
      seed-text: "foo0"
      nonce: 0
      amount: 10000000000000000
    }
  }
}
```

## Шаг 4

Выполните команду генератора генезис блока:

```sbt "node/runMain com.wavesplatform.GenesisBlockGenerator node/src/test/resources/genesis.example.conf genesis.conf"```

Результат будет записан в файле `genesis.conf` (вместо `genesis.conf`, может быть произволное название), и будет выглядет примерно так:

```bash
Addresses:
foo0:
 Seed text:           foo0
 Seed:                3csAfH
 Account seed:        58zgAnBg775J6NKd4qVtfeX3m5TBMeizHNY9STvm2N87
 Private account key: FYLXp1ecxQ6WCPD4axTotHU9RVfPCBLfSeKx1XSCyvdT
 Public account key:  GbGEY3XVc2ohdv6hQBukVKSTQyqP8rjQ8Kigkj6bL57S
 Account address:     3JfE6tjeT7PnpuDQKxiVNLn4TJUFhuMaaT5
Settings:
genesis {
  average-block-delay: 60000ms
  initial-base-target: 153722867
  timestamp: 1500635421931
  block-timestamp: 1500635421931
  signature: "3NELFXiQqQoYUfgLba5YAS1z8gJLc19zfzSvmYRX9eLso4zGByRGDpWdL4cooHTocyi5boFiu6H7hyW3ukVGtswP"
  initial-balance: 10000000000000000
  transactions = [
    {recipient: "3JfE6tjeT7PnpuDQKxiVNLn4TJUFhuMaaT5", amount: 10000000000000000}
  ]
}
```

Если вы собрали fat JAR, вы можете сгенерировать генезис блок.

**Пример**:

```bash
java -cp ./node/target/waves-all-0.17.2-grpc-27-g0fab715-DIRTY.jar com.wavesplatform.GenesisBlockGenerator node/src/test/resources/genesis.example.conf
```

Вывод будет таким же.

## Шаг 5

Создайте файл `*.conf` с любым именем (например `waves-custom-network.conf`) и откройте его в любом текстовом редакторе.

Вы можете включить следующую функциональность ноды, редактируя в файле параметр `pre-activated-features`.

| Функциональность | Имя | Статус |
|---|---|---|
| 1 | Минмальный генерирующий баланс 1000 WAVES | ACTIVATED |
| 2 | NG Протокол | ACTIVATED |
| 3 | Транзакции массовой рассылки | ACTIVATED |
| 4 | Smart аккаунты | ACTIVATED |
| 5 | Data транзакции | ACTIVATED |
| 6 | Сжигать любые токены | ACTIVATED |
| 7 | Спонсорская комиссия | ACTIVATED |
| 8 | Fair PoS | ACTIVATED |
| 9 | Smart ассеты | ACTIVATED |
| 10 | Smart аккаунт торговля | ACTIVATED |

> Если параметр директории не был изменён, то папка waves будет создана по адресу
<br>Linux: $XDG_DATA_HOME/waves or $HOME/.local/share/waves
<br>Win: %APPDATA%/local/waves
<br>macOS: $HOME/Library/Application Support/waves

> Значение параметра `address-scheme-character` ниже, должно совпадать со значением `network-type` из **Шага 3**.

> Содержимое секции `genesis` ниже это то, что было сгенерировано в **Шаге 4**. Вместо того, чтобы вставить эту секцию, можно написать `include "genesis.conf"`, где `genesis.conf` это имя файла из **Шага 4**.

```bash
# Настройки ноды Waves
waves
{
  # папка для хранения данных
  directory=/tmp/custom

  logging-level = DEBUG

  blockchain
  {
    type: CUSTOM
    custom
    {
      address-scheme-character: "L" # это значение должнол быть таким же как значение `network-type` из **Шага 3**
      # различные параметры консенсуса сети
      functionality {
        feature-check-blocks-period = 30
        blocks-for-feature-activation = 25
        allow-temporary-negative-until: 0
        allow-invalid-payment-transactions-by-timestamp: 0
        require-sorted-transactions-after: 0
        generation-balance-depth-from-50-to-1000-after-height: 0
        minimal-generating-balance-after: 0
        allow-transactions-from-future-until: 0
        allow-unissued-assets-until: 0
        require-payment-unique-id-after: 0
        allow-invalid-reissue-in-same-block-until-timestamp: 0
        allow-multiple-lease-cancel-transaction-until-timestamp: 0
        reset-effective-balances-at-height: 1
        allow-leased-balance-transfer-until: 0
        block-version-3-after-height: 0
        pre-activated-features = {
          2 = 0
        }
        double-features-periods-after-height = 1000000000
        max-transaction-time-back-offset = 120m
        max-transaction-time-forward-offset = 90m
      }
      genesis {
        average-block-delay: 60000ms
        initial-base-target: 153722867
        timestamp: 1500635421931
        block-timestamp: 1500635421931
        signature: "3NELFXiQqQoYUfgLba5YAS1z8gJLc19zfzSvmYRX9eLso4zGByRGDpWdL4cooHTocyi5boFiu6H7hyW3ukVGtswP"
        initial-balance: 10000000000000000
        transactions = [
          {recipient: "3JfE6tjeT7PnpuDQKxiVNLn4TJUFhuMaaT5", amount: 10000000000000000}
        ]
      }
      # содержимое секции `genesis` выше это то, что было сгенерировано в **Шаге 4**
      # обратите внимание, что вместо того, чтобы вставить эту секцию, ы можете написать
      # `include "genesis.conf"`, где `genesis.conf` это имя файла из **Шага 4**
    }
  }

  network
  {
    bind-address = "0.0.0.0"
    port = 6860
    known-peers = []
    node-name = "L custom node 1"
    declared-address = "127.0.0.1:6860"
  }

  wallet
  {
    password = "password"
    seed = "3csAfH"
  }

  rest-api
  {
    # Enable/disable REST API
    enable = yes
    # Сетевой адрес для привязки
    bind-address = "0.0.0.0"
    # Порт для приема запросов REST API
    port = 6861
    # Hash строки ключа API
    api-key-hash = "H6nsiifwYKYEx6YzYD7woP1XCn72RVvx6tC1zjjLXqsu"
  }

  miner
  {
    # Разрешить генерацию блока только в последнем блоке не старше указанного периода времени
    interval-after-last-block-then-generation-is-allowed = 999d
    # Требуемое количество подключений (как входящих, так и исходящих) для создания блока. Установка этого значения 0
    # включит "off-line генерацию".
    quorum = 0
  }
}
```

Будьте внимательны с параметрами `waves.blockchain.custom.address-scheme-character` и `waves.blockchain.custom.genesis`. Они были скопированы из результатов и и настроек инструмента генезис генерации. Также, посмотрите на значение `waves.wallet.seed`. Это значение может быть скопированно из значения "Seed" для одного из генезис адресов из результатов инструмента генезис генерации.

## Шаг 6

Запустите свою сеть выполнив команду:

```sbt "node/run waves-custom-network.conf"```

Также, вы можете запустить уже собранный релиз (deb или jar) с помощью этого файла конфигурации вручную.

## Добавить ноды в вашу сеть

Вы можете добавить больше нод в вашу сеть с помощью параметра `waves.network.known-peers`, задать адрес и порт существующей нода с такими же сетевыми параметрами как "127.0.0.1:6860". Если вы создаёте несколько локальных нод, не забудьте поменять для новых нод сетевой порт `waves.network.port`, порт API `waves.rest-api.port`, папку для данных `waves.directory` и seed кошелька `waves.wallet.seed`.

Секция `waves.blockchain.custom.functionality` сожержит параметры, которые позволяют включить или выключить функциональность вашей блокчейн системы.

**Примечание**: Разработчики могут добавлять новые параметры в секции `waves.blockchain.custom.functionality`, которых нет в данном примере; в качестве примера рабочей конфигурации, пожно использовать[waves-devnet.conf файл в корневой папке репозитория](https://github.com/wavesplatform/Waves/blob/master/node/waves-devnet.conf).

Больше информации в статье [Конфигурация ноды](/en/waves-node/node-configuration).
