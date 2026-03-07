---
icon: family
---

# entity

Executes every time when basic entity data was retrieved.



```lua
pre_entities()
entity(entity: entity, name_hash: hash_t)
post_entities()
```



This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

```lua
local health_offset = schema.get("C_BaseEntity", "m_iHealth")
local weapon_c4_hash = make_hash("weapon_c4")

local c4_health = {}

local function on_pre_entities()
    c4_health = {}
end

local function on_entity(entity, name_hash)
    if name_hash ~= weapon_c4_hash
        return    
    end

    local health = entity:get_int(health_offset)
    c4_health[entity:get_index()] = health
end

set_callback("pre_entities", on_pre_entities)
set_callback("entity", on_entity)
```
