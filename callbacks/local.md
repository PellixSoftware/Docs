---
icon: location-dot
---

# local

Executes every time when basic local player data was retrieved.

```lua
local(player: entity)
```



&#x20;This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

```lua
local health_offset = schema.get("C_BaseEntity", "m_iHealth")

local function on_local(player)
    local health = player:get_int(health_offset)
    print(health)
end

set_callback("local", on_local)
```
