---
description: Interface to perform operations with entities.
icon: people-group
---

# entitylist

Note: Please do not use entity list functions unless absolutely needed! Players can be fetched from [player](../callbacks/player.md) and [local](../callbacks/local.md) callbacks, entities can be fetched from [entity](../types/entity/) callback, they provide already known entities with their respective addresses, iterating entity list manually is _**never**_ a good idea.



**Functions:**

```lua
entitylist.get_base(index: number [, cached: boolean = false]): uintptr_t | nil
```

Returns entity base by index.



```lua
entitylist.get_base_from_handle(handle: number [, cached: boolean = false]): uintptr_t | nil
```

Returns entity base from handle.<br>

