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
    local movetype = player:get_movetype()
    print(movetype)
end)

-- vector<3>
local vector3_meta = get_builtin_metatable("vector<3>")

vector3_meta.length_fast = function(self)
    return self.x * self.x + self.y * self.y + self.z * self.z
end

local pos = vector.new(1, 2, 3)
print(pos.length_fast())
```

