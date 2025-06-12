# State Machine

Blockchain development can be model as a State Machine.

The set of all the functions deployed on chain is the State Transfer Function (STF) of a State Machine.



The State Machine comes with the basic concepts, an **Input** is applied to the **Current State**, under the rule of **State Transfer Function** to transit the **Current State** into a **New State**.

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>State Machine</p></figcaption></figure>



Here is an example, let's assume we have a **Current State** of block number 100:

```json
{
   Alice's USDC Balace: 50,
   Bob's USDC Balace: 200,
}
```

While in the block 100, Bob is sending a transaction to move USDC balance from Bob to Alice:

```json
{"p": "zen", "f": "transfer", "a": ["USDC", "Alice", 100]}
```

The `transfer` function is accepting the transaction as the Input of **State Machine**, outputs a **New State:**

```json
{
   Alice's USDC Balace: 150,
   Bob's USDC Balace: 100,
}
```

As an example, we can take a look how the `transfer` STF is written in python:

```python
def transfer(info, args):
    sender = info['sender']
    tick = args['a'][0]
    receiver = args['a'][1].lower()
    value = int(args['a'][2])
    assert value > 0

    sender_balance = get(tick, 'balance', 0, addr)
    assert sender_balance >= value
    sender_balance -= value
    put(addr, tick, 'balance', sender_balance, addr)
    receiver_balance = get(tick, 'balance', 0, receiver)
    receiver_balance += value
    put(receiver, tick, 'balance', receiver_balance, receiver)
```

This is a very basic function, we use `get` and `put` API calls here. For the security reason, we should do more check for the arguments.
