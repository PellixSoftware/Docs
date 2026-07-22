---
description: Allow to access virtual memory.
icon: microchip
---

# memory

**NOTE: Please do not use memory functions from** [**draw**](../callbacks/draw.md) **and** [**draw3d**](../callbacks/draw3d.md) **callbacks. This will work but it's highly not recommended as it may slow down the overlay thread when used extensively.**



**Functions:**

```lua
memory.read(base: uintptr_t, size: size_t): string.buffer
```

Reads a piece of memory from the virtual address space of the target process, returns [LuaJIT string buffer](https://luajit.org/ext_buffer.html).



```lua
memory.read_byte(base: number): number -- 1 byte
memory.read_word(base: number): number -- 2 bytes
memory.read_dword(base: number): number -- 4 bytes 
memory.read_ptr(base: number): uintptr_t -- pointer size bytes
memory.read_float(base: number): number -- 4 byte float
memory.read_double(base: number): number -- 8 byte double precision float
```

Reads common value types from the target's process memory.



```lua
memory.get_module(name: string): uintptr_t, number

-- Example:
local base, size = memory.get_module("client.dll")
print("client.dll at: ", base, ", size: ", size)
```

Retrieves basic module information from the target process.



