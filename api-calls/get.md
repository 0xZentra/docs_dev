# get

Assuming you are familiar with [State Machine](../state-machine.md), the development of Zentra function is always involving read and write the global state. The `get` function provides the way to access the state.

```python
def get(_asset, _var, _default = None, _key = None):
```

### Parameters



### Example



### Further Reading

In Ethereum, the global state is stored in complex encoding such as ABI or RLP, then they would be stored in MPT structure for versioning and verification purpose. Unlike Ethereum, Zentra designs the global state in a transparent way. Users do not need to write a view function to extra the global state's value, it can be retrieved with HTTP API query in the indexer.
