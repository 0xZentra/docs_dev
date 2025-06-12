# Python

Zentra is building with CPython version 3.10 under a standard Ubuntu 22.04 LTS version.

A Windows WSL environment is recommend, and [https://canonical.com/multipass](https://canonical.com/multipass) is recommend when WSL is not available (for Windows and Mac).



For the playground, CPython 3.10 is recommend:

* Standard python 3.10.x [https://www.python.org/downloads/release/python-31018/](https://www.python.org/downloads/release/python-31018/)
* Windows Store [https://apps.microsoft.com/detail/9pjpw5ldxlz5](https://apps.microsoft.com/detail/9pjpw5ldxlz5)
* UV to manage multi versions in local [https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)



To start the development, it is briefly to create a new function in python, which will make changes to the current global state from a block transaction. If you are not familiar with State Machine concept, please check the next paragraph for a simple tutorial of [State Machine Concept](../state-machine.md).

```python
def a_new_function(info, args):
    pass
```

The parameters are fixed: `info` will provide the blockchain related information and `args` will contains the arguments you passed for the function invoke to Zentra.



By using python, we allow developers to use almost all the native python syntax except the `import` and `class` keywords. Most of the built-in function are allowed, but we do not provide `open` and other risk functions. The python code would be convert into python bytecode, thus most of dynamic feature would be kept, like infinite integer and list, dict, set, tuple.



