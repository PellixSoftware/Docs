---
description: Interface to perform operations with entities.
icon: people-group
---

# entitylist

**Functions:**

```lua
entitylist.get_base(index: number [, cached: boolean = false]): uintptr_t | nil
```

Returns entity base by index.



```lua
entitylist.get_base_from_handle(handle: number [, cached: boolean = false]): uintptr_t | nil

-- Example
local handle_offset = schema.get("CCSPlayerController", "m_hPawn")
local controller_base = entitylist.get_base(1)
local handle = memory.read_dword(controller_base + handle_offset)
entitylist.get_base_from_handle(handle) -- 0x228E9B24000
```

Returns entity base from handle.<br>

\
\`
