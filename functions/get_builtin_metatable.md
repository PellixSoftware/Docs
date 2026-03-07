# get\_builtin\_metatable

Retrieves internal meta tables for builtin types.

This can be useful if you want to extend basic types functionality, see  [extending-builtin-types.md](../examples/extending-builtin-types.md "mention").

&#x20;:warning: **Warning:** Please do not change `__index`  value in this meta table or you'll lose access to the builtin members.



```lua
get_builtin_metatable(name: string): table | nil
```



**Available meta tables:**

* entity
* vector<2>
* vector<3>
* vector<4>
