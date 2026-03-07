---
description: This structure describes entity.
icon: user
---

# entity

**Functions:**

```lua
entity:get_base(): uintptr_t
```

Returns entity base address.



```lua
entity:get_index(): number
```

Returns entity index.



```lua
entity:get_class_name_hash(): hash_t
```

Returns entity class name hash, may return 0 for entity which wasn't cached.



```lua
entity:is_alive(): boolean
```

Checks if entity is alive.



```lua
entity:get_abs_origin(): number, number, number
```

Retrieves entity absolute origin (`CGameSceneNode::m_vecAbsOrigin`)



### **Read primitives:**

```lua
entity:read(offset: number, size: number): string.buffer
```

Retrieves a chunk of memory from the entity.



```lua
entity:get_ushort(offset: number): number
```

Retrieves an unsigned 16-bit integer value from the entity's memory specified by an offset.



```lua
entity:get_int(offset: number): number
```

Retrieves a signed 32-bit integer value from the entity's memory specified by an offset.



```lua
entity:get_ptr(offset: number): uintptr_t
```

Retrieves a pointer value from the entity's memory specified by an offset.



```lua
entity:get_float(offset: number): number
```

Retrieves a floating point value from the entity's memory specified by an offset.



```lua
entity:get_bool(offset: number): boolean
```

Retrieves a boolean value from the entity's memory specified by an offset.



```lua
entity:get_vector2(offset: number): number, number
```

Retrieves a two-dimensional vector value from the entity's memory specified by an offset.



```lua
entity:get_vector3(offset: number): number, number, number
```

Retrieves a three-dimensional vector value from the entity's memory specified by an offset.



```lua
entity:get_vector4(offset: number): number, number, number, number
```

Retrieves a four-dimensional vector value from the entity's memory specified by an offset.



