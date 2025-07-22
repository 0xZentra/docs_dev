# get

Assuming you are familiar with [State Machine](../state-machine.md), the development of Zentra function is always involving read and write the global state. The `get` function provides the way to access the state.

```python
def get(_asset, _var, _default = None, _key = None):
```

### Parameters

*   `_asset` (str): The unique tick of the asset you want to query (e.g., "USDC", "function").
*   `_var` (str): The name of the state variable to retrieve (e.g., "total_supply").
*   `_default` (any, optional): The value to return if the requested state variable is not found. Defaults to `None`.
*   `_key` (str, optional): A sub-key for accessing data within a variable, similar to a dictionary key. This is useful for mapping-like structures, such as retrieving the balance of a specific address.

### Example

While any global state can be read directly via off-chain APIs, `get` is essential for on-chain functions that need to read state to perform calculations or enforce validation, such as in a `transfer` function.

This example shows how `get` is used within a `transfer` function to read balances before executing the state change with `put`.

```python
def transfer(info, args):
    sender = info['sender']
    asset_tick = args[0]
    receiver_handle = args[1]
    amount = int(args[2])

    assert amount > 0, "Transfer amount must be positive."

    # Get the sender's balance to verify they have enough funds.
    # This is a critical on-chain check.
    sender_balance = get(asset_tick, "balance", 0, sender)
    assert sender_balance >= amount, "Insufficient balance."

    # Get the receiver's current balance.
    receiver_balance = get(asset_tick, "balance", 0, receiver_handle)

    # Calculate new balances
    new_sender_balance = sender_balance - amount
    new_receiver_balance = receiver_balance + amount

    # Update the state for both sender and receiver
    put(sender, asset_tick, "balance", new_sender_balance, sender)
    put(receiver_handle, asset_tick, "balance", new_receiver_balance, receiver_handle)

    print(f"Successfully transferred {amount} {asset_tick} from {sender} to {receiver_handle}.")
```

### Further Reading

In Ethereum, the global state is stored in complex encoding such as ABI or RLP, then they would be stored in MPT structure for versioning and verification purpose. Unlike Ethereum, Zentra designs the global state in a transparent way. Users do not need to write a view function to extra the global state's value, it can be retrieved with HTTP API query in the indexer.
