---
description: This example shows how to extend basic types for your needs.
---

# Extending builtin types

```lua
-- entity
local entity_meta = get_builtin_metatable("entity")
local movetype_offset = schema.get("C_BaseEntity", "m_MoveType")

entity_meta.get_movetype = function(self)
    return self:get_int(movetype_offset)
end

set_callback("player", function(player)
    local pawn = player:get_pawn()
    local movetype = pawn:get_movetype()
    print(movetype)
end)
```

