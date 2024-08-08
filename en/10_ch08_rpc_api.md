# 8. RPC API do Bitcoin Core

Bitcoin Core implements a JSON-RPC interface that can be accessed using the ```bitcoin-cli``` command-line tool. This interface allows you to interactively experiment with the functionalities available programmatically via API.

After installing Core and starting it with the command ```bitcoind -daemon```, you can begin calling RPC (Remote Procedure Call) commands. It is also possible to access directly via HTTP using curl.

### Basic RPC Commands

Bitcoin Core's RPC commands allow you to interactively explore the blockchain, verify transactions, and obtain detailed information about the network and wallet state. To see a list of available commands, use:
```bitcoin-cli help```

Here are some useful commands:

- ```bitcoin-cli getbestblockhash```: Returns the hash of the best block in the blockchain.
- ```bitcoin-cli getblock "blockhash"```: Retrieves information about a specific block given its hash.
- ```bitcoin-cli getblockchaininfo```: Displays detailed information about the state of the blockchain.
- ```bitcoin-cli getnetworkinfo```: Displays basic information about the Bitcoin network node status.
- ```bitcoin-cli getrawtransaction "txid"```: Returns a raw transaction in hexadecimal notation.
- ```bitcoin-cli decoderawtransaction "hex"```: Decodes a raw transaction from hexadecimal to JSON.
- ```bitcoin-cli walletpassphrase "passphrase" timeout```: Unlocks the wallet and keeps it unlocked for a specific period.
- ```bitcoin-cli walletpassphrasechange "oldpassphrase" "newpassphrase"```: Changes the wallet password.
- ```bitcoin-cli walletprocesspsbt "psbt"```: Processes a Partially Signed Bitcoin Transaction (PSBT).
- ```bitcoin-cli getblockhash 1000```: Gets the block hash at height 1000.
- ```bitcoin-cli getblock "blockhash"```: Gets block details using its hash.
- ```bitcoin-cli getrawtransaction "txid"```: Gets and decodes a transaction using its ID.
- ```bitcoin-cli decoderawtransaction "hex"```: Decodes a raw transaction from hexadecimal to JSON.
- ```bitcoin-cli getnetworkinfo```: Gets information about the network node status.

Using these commands through the command line or programmatically via API allows Bitcoin developers and enthusiasts to interact directly with the network, validating and exploring data independently and securely. See more at [https://developer.bitcoin.org/reference/rpc/](https://developer.bitcoin.org/reference/rpc/)
