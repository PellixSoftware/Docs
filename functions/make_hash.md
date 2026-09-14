# make\_hash

Makes hash from value for internal usage.

Underlying implementation uses crc64 but this may change.



```lua
make_hash(text: string): uint64_t
make_hash(buffer: string.buffer): uint64_t
```



**Example:**

```lua
local weapon_c4_hash = make_hash("weapon_c4") 
```
