# put

The `put` function provides the way to update global state.

```python
def put(_owner, _asset, _var, _value, _key = None):
```

### Parameters

*   `_owner` (str): The handle or address of the entity that owns and authorizes the state change. The state is always recorded under this owner's name.
*   `_asset` (str): The unique tick of the asset you want to modify (e.g., "USDC", "function").
*   `_var` (str): The name of the state variable to update (e.g., "balance").
*   `_value` (any): The new value to be stored. It can be any JSON-serializable type.
*   `_key` (str, optional): A sub-key for updating a specific entry within a variable. This is essential for updating a single user's balance in a balances mapping.

### Example

This example shows how to implement a basic `mint` function, where an admin increases the total supply of a token and updates a user's balance.

```python
def mint(info, args):
    # The sender must be the admin of the asset
    admin = info['sender']
    
    # Arguments for the mint function
    receiver_handle = args[0]
    amount = int(args[1])

    # Ensure the amount is positive
    assert amount > 0, "Cannot mint a zero or negative amount."

    # Get the current total supply
    total_supply = get("ZENT", "total_supply", 0)
    new_total_supply = total_supply + amount

    # Get the receiver's current balance
    receiver_balance = get("ZENT", "balance", 0, receiver_handle)
    new_receiver_balance = receiver_balance + amount

    # Update the state using put
    # The admin (sender) authorizes the change
    put(admin, "ZENT", "total_supply", new_total_supply)
    put(admin, "ZENT", "balance", new_receiver_balance, receiver_handle)

    print(f"Successfully minted {amount} ZENT to {receiver_handle}.")
```

