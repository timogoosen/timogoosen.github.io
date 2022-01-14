## Web3Py Examples:


Connect to Polygon Testnet with Web3py without infura:

```
#!/usr/bin/env python3

from ethtoken.abi import EIP20_ABI
from web3 import Web3


token_to_private_key = "REDACTED"



polygon_chain_url = "https://rpc-mumbai.maticvigil.com"
w3 = Web3(Web3.HTTPProvider(polygon_chain_url))


print(w3.isConnected())
print(w3.eth.blockNumber)

balance = w3.eth.getBalance("0xcCF9145887927EEB0308833f1e90CAEDB678a922") # This is the address of the wallet/private key you are using
print(w3.fromWei(balance, "ether"))  # We are on Polygon so it thinks "ether" is MATIC. So just use ether here to check MATIC balance.

````