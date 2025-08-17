---
description: >-
  This API provides objects for interacting with various entities within the
  game world, such as players, weapons, and props. These objects are wrappers
  around the game's internal data structures.
---

# Game Objects

## Common Methods: Generic Data Access

All major game objects (`Entity`, `PlayerPawn`, `WeaponBase`, `PlayerController`) share a set of generic methods for reading data at a specific memory offset from the object's base address. This is a powerful feature for accessing data that is not available through a dedicated function, using offsets retrieved from the `Schema` API.

| Function                       | Description                                             |
| ------------------------------ | ------------------------------------------------------- |
| `instance:GetInt(Offset)`      | Reads a 4-byte signed integer.                          |
| `instance:GetFloat(Offset)`    | Reads a 4-byte single-precision float.                  |
| `instance:GetDouble(Offset)`   | Reads an 8-byte double-precision float.                 |
| `instance:GetBool(Offset)`     | Reads a 1-byte boolean value.                           |
| `instance:GetChar(Offset)`     | Reads a 1-byte character.                               |
| `instance:GetPtr(Offset)`      | Reads a memory address. Returns a new `Pointer` object. |
| `instance:GetLVector3(Offset)` | Reads three consecutive floats as a `Vector3`.          |

**Example Usage:**

```lua
-- Assume LocalPlayer is a PlayerPawn object
-- First, get the offset for the 'm_fFlags' member using the Schema API
local FlagsOffset = Schema:GetC("C_BaseEntity", "m_fFlags")

OnLocalPlayer:RegisterCallback(Controller, Pawn)
    -- Now, use the generic getter on the player instance to read the value at that offset
    local PlayerFlags = Pawn:GetInt(FlagsOffset)
    
    -- Check if the first bit is set (player is on the ground)
    if (PlayerFlags & 1) == 1 then
        print("Player is on the ground.")
    end
end)
```
