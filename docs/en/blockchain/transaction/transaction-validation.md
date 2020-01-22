# Transaction Validation

## Default Transaction Validation

After creation of Waves account, each transaction outgoing from this account is checked for validity. If a transaction is valid, then it makes it to a generated block in the blockchain, if not — it is rejected by the blockchain.

By default, _only_ the fact that an outgoing transaction belongs to the owner of the account it was sent from, is checked. To check that, the transaction's binary data, the account owner's public key and the digital signature of the transaction are run through special `sigVerify` function. If the `sigVerify` function returns `true` — the transaction is considered valid, otherwise — invalid.

## Transaction Validation Using Account Script

If the validation logic goes beyond the detection of transaction ownership, then a programmer writes [account script](/en/ride/script/script-types/account-script) that contains that logic. This script is attached to the account making this account a [smart account](/en/blockchain/account/smart-account). Now it's account script's duty to validate all the outgoing transactions from the account. Still, the `sigVerify` function is widely used by programmers inside of the account script.
