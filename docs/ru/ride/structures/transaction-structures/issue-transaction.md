# IssueTransaction

Структура [транзакции выпуска](/ru/blockchain/transaction-type/issue-transaction).

## Конструктор

``` ride
IssueTransaction(quantity: Int, name: ByteVector, description: ByteVector, reissuable: Boolean, decimals: Int, script: ByteVector|Unit, id: ByteVector, fee: Int, timestamp: Int, version: Int, sender: Address, senderPublicKey: ByteVector, bodyBytes: ByteVector, proofs: List[ByteVector])
```

## Поля структуры

| # | Название | Тип данных | Описание |
| :--- | :--- | :--- | :--- |
| 1 | quantity | [Int](/ru/ride/data-types/int) | Количество [токена](/ru/blockchain/token) |
| 2 | name | [ByteVector](/ru/ride/data-types/byte-vector) | Название токена |
| 3 | description | [ByteVector](/ru/ride/data-types/byte-vector) | Описание токена |
| 4 | reissuable | [Boolean](/ru/ride/data-types/boolean) | Флаг возможности довыпуска токена |
| 5 | decimals | [Int](/ru/ride/data-types/int) | Число знаков после запятой |
| 6 | script | [ByteVector](/ru/ride/data-types/byte-vector)&#124;[Unit](/ru/ride/data-types/unit) | [Скрипт ассета](/ru/ride/script/script-types/asset-script) |
| 7 | id | [ByteVector](/ru/ride/data-types/byte-vector) | [ID транзакции](/ru/blockchain/transaction/transaction-id) |
| 8 | fee | [Int](/ru/ride/data-types/int) | [Комиссия за транзакцию](/ru/blockchain/transaction/transaction-fee) |
| 9 | timestamp | [Int](/ru/ride/data-types/int) | [Временная метка транзакции](/ru/blockchain/transaction/transaction-timestamp) |
| 10 | version | [Int](/ru/ride/data-types/int) | [Версия транзакции](/ru/blockchain/transaction/transaction-version) |
| 11 | sender | [Address](/ru/ride/structures/common-structures/address) | [Адрес](/ru/blockchain/account/address) отправителя транзакции |
| 12 | senderPublicKey | [ByteVector](/ru/ride/data-types/byte-vector) | Открытый ключ отправителя транзакции |
| 13 | bodyBytes | [ByteVector](/ru/ride/data-types/byte-vector) | [Байты тела транзакции](/ru/blockchain/transaction/transaction-body-bytes) |
| 14 | proofs | [List](/ru/ride/data-types/list)[[ByteVector](/ru/ride/data-types/byte-vector)] | Список [подтверждений](/ru/blockchain/transaction/transaction-proof) |
