# Basic Concept

Zentra work with existing ETH compatible blockchain, but providing a non-EVM Python virtual machine. It means existing popular library like web3.py and ethers.js can be used for blockchain development. The development language is standard native python. It is the dynamic CPython with [python bytecode](https://docs.python.org/3.10/library/dis.html) instead of other python-like static languages like Vyper. On chain smart-contract (function in Zentra) development must be done in python.

The blockchain is modeled as a **State Machine**. We build functions in python to apply the change to the state with the ordered transactions in a block.

A Zentra transaction customs CALLDATA talking to ETH RPC. It is in JSON format:

```json
{"p": "zen", "f": "token_create", "a": ["ZENT", "Zentra", 18]}
```

**p** stands for the protocol, it should be **zen** for mainnet.&#x20;

**f** stands for the function to call, it's a string.

**a** stands for the arguments, it should be a list.



