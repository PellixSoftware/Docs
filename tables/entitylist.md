---
description: Interface to perform operations with entities.
icon: people-group
---

# entitylist

**NOTE: Please do not use entitylist functions from** [**draw**](../callbacks/draw.md) **and** [**draw3d**](../callbacks/draw3d.md) **callbacks. This will work but it's highly not recommended as it may slow down the overlay thread when used extensively.**



**Functions:**

```lua
entitylist.get_base(index: number [, cached: boolean = false]): uintptr_t | nil
```

Returns entity base by index.



```lua
entitylist.get_base_from_handle(handle: number [, cached: boolean = false]): uintptr_t | nil
```

Returns entity base from handle.<br>

