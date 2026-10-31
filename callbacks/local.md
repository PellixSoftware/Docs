---
icon: location-dot
---

# local

Executes every time when basic local player data was retrieved, player references in-game `CCSPlayerController`.

In single thread mode always fires between [pre\_players](player.md) and [post\_players](player.md), order is not guaranteed otherwise.

```luau
local(player: entity)
```



&#x20;This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

```lua
local ping_offset = schema.get("CCSPlayerController", "m_iPing")

local function on_local(player)
    local ping = player:get_int(ping_offset)
    print(ping)
end

set_callback("local", on_local)
```

