# Playground

Zentra provides the playground in web and local for the developers and users to test the features.

{% embed url="https://playground.zentra.dev/" fullWidth="false" %}
Zentra web playground is easy to use without anything installed local
{% endembed %}

With Zentra playground, users and developers can easily experience Zentra system without running the full stack in local.&#x20;

Here we provide some cheat sheet for you to firstly steps in the web playground:

```python
asset_create("USDC")
token_create("USDC", "Mock USDC", 6)
token_mint_once("USDC", 10000000000)
transfer("USDC", "0xbob", 5000000000)
```

Executing the functions one by one and see the global state changes, and check the code you are invoking on the left, before you start to create your own function.



If you are familiar with local development environment and terminal, check out [https://github.com/ZentraPoW/zentra\_playground](https://github.com/ZentraPoW/zentra_playground) .
