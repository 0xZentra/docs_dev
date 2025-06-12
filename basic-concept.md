# Basic Concept

Zentra ships with a built-in Python VM. The development language is standard native python. It is the dynmaic cpython with [python bytecode](https://docs.python.org/3.10/library/dis.html) instead of other python-like static languages.

The blockchain is modeled as a state machine. We build functions in python to apply the change to the state with the ordered transactions in current block.

A transaction is the CALLDATA in ETH RPC, it is in json format:

```json
{"p": "zen", "f": "token_create", "a": ["ZENT", "Zentra", 18]}
```

**p** stands for the protocol, it should be **zen** for mainnet.&#x20;

**f** stands for the function to call, it's a string.

**a** stands for the arguments, it should be a list.



