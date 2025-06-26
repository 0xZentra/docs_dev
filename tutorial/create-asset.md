# Create Asset

In Zentra, **asset** is the basic concept. The **asset** can be a token, dapp or brand, etc.

The **asset** is tick starting with uppercase and digital. However, it is possible to just create **asset** without being a token.



Once we check the global state to make sure the **asset** name was not taken by others, we can use **asset\_create** function to create it. You can try this in Zentra playground.

In testnet, we can send a transaction with CALLDATA, for example:

```json
{"p": "zen", "f": "asset_create", "a": ["USDC"]}
```

