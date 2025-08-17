---
description: >-
  The Memory is a global object that provides all the functions needed to read
  from, write to, and search within the application's memory. It operates using
  the Pointer objects.
---

# Memory

## Memory Reading

{% hint style="info" %}
You very rarely need to call these functions yourself, prefer using reads from entities directly as those are cached. **Each** of these functions are an actual **memory read request**.
{% endhint %}

These functions read a value of a specific data type from a given memory address.

| Function                       | Description                                                       |
| ------------------------------ | ----------------------------------------------------------------- |
| `ReadChar(address)`            | Reads a 1-byte signed integer.                                    |
| `ReadUChar(address)`           | Reads a 1-byte unsigned integer.                                  |
| `ReadShort(address)`           | Reads a 2-byte signed integer.                                    |
| `ReadUShort(address)`          | Reads a 2-byte unsigned integer.                                  |
| `ReadInt(address)`             | Reads a 4-byte signed integer.                                    |
| `ReadUInt(address)`            | Reads a 4-byte unsigned integer.                                  |
| `ReadFloat(address)`           | Reads a 4-byte single-precision float.                            |
| `ReadDouble(address)`          | Reads an 8-byte double-precision float.                           |
| `ReadPointer(address)`         | Reads a memory address (pointer). Returns a new `Pointer` object. |
| `ReadString(address, maxSize)` | Reads a null-terminated string up to `maxSize` bytes.             |

**Example:**

```lua
-- Assume LocalPlayerPointer is a Pointer object to the local player
-- and HealthOffset is the number we got from Schema
local HealthAddress = LocalPlayerPointer + HealthOffset
local CurrentHealth = Memory:ReadInt(HealthAddress)

print("Current Health: " .. CurrentHealth)

-- Reading a name from a pointer at another offset
local NameOffset = Schema:GetC("C_BasePlayer", "m_szCustomName")
local PlayerName = Memory:ReadString(LocalPlayerPointer + NameOffset, 64)
```

## Memory Writing

{% hint style="info" %}
These are not currently implemented in the cheat, **calling them won't do anything**. They are only already here for future versions.
{% endhint %}

These functions write a given value to a specific memory address.

| Function                       | Description                                                         |
| ------------------------------ | ------------------------------------------------------------------- |
| `WriteChar(address, value)`    | Writes a 1-byte signed integer.                                     |
| `WriteUChar(address, value)`   | Writes a 1-byte unsigned integer.                                   |
| `WriteShort(address, value)`   | Writes a 2-byte signed integer.                                     |
| `WriteUShort(address, value)`  | Writes a 2-byte unsigned integer.                                   |
| `WriteInt(address, value)`     | Writes a 4-byte signed integer.                                     |
| `WriteUInt(address, value)`    | Writes a 4-byte unsigned integer.                                   |
| `WriteFloat(address, value)`   | Writes a 4-byte single-precision float.                             |
| `WriteDouble(address, value)`  | Writes an 8-byte double-precision float.                            |
| `WritePointer(address, value)` | Writes a memory address from a `Pointer` object.                    |
| `WriteString(address, value)`  | Writes a string to memory. **Warning:** Does not check buffer size. |

**Example:**

```lua
-- Set player health to 100
local HealthAddress = LocalPlayerPointer + HealthOffset
Memory:WriteInt(HealthAddress, 100)
```

## Utilities

**`Memory:GetModuleBase(ModuleName)`**

Finds the base address of a loaded module (e.g., a DLL).

* **ModuleName:** (`string`) The name of the module (e.g., `"engine.dll"`).
* **Returns:** (`Pointer`) A `Pointer` object to the base address of the module, or a null pointer if not found.

```lua
local ClientBase = Memory:GetModuleBase("client.dll")
if ClientBase then
    print("Client.dll is loaded at: " .. ClientBase)
end
```

**`Memory:GetModuleSize(ModuleName)`**

Finds the total size in memory of a loaded module.

* **ModuleName:** (`string`) The name of the module.
* **Returns:** (`Pointer`) A `Pointer` object whose "address" is the size of the module.

```lua
local ClientBase = Memory:GetModuleBase("client.dll")
local ClientSize = Memory:GetModuleSize("client.dll")
```

**`Memory:ScanPattern(Base, Size, Pattern)`**

Searches a region of memory for a specific sequence of bytes (pattern).

* **Base:** (`Pointer`) The starting address for the scan.
* **Size:** (`number` or `Pointer`) The number of bytes to scan.
* **Pattern:** (`string`) The byte pattern to search for. Use `?` or `??` for wildcards (bytes that can be any value). Bytes are specified in hex, separated by spaces.
* **Returns:** (`Pointer`) The address where the pattern was found, or a null pointer if not found.

```lua
local ClientBase = Memory:GetModuleBase("client.dll")
local ClientSize = Memory:GetModuleSize("client.dll")

-- Scan for a unique function signature inside the client.dll module
local Pattern = "55 8B EC 83 E4 F8 83 EC 7C 53 56"
local FunctionAddress = Memory:ScanPattern(ClientBase, ClientSize, Pattern)

if FunctionAddress then
    print("Found function at: " .. FunctionAddress)
end
```

**`Memory:GetModuleExport(ModuleName, ExportName)`**

Retrieves the address of an exported function or variable from a module.

* **ModuleName:** (`string`) The name of the module.
* **ExportName:** (`string`) The name of the exported function/variable.
* **Returns:** (`Pointer`) The address of the export, or a null pointer if not found.

```lua
-- Get the "CreateInterface" function from tier0.dll
local CreateInterfaceAddress = Memory:GetModuleExport("tier0.dll", "CreateInterface")
```

**`Memory:ProtectVirtualMemory(Address, Size, NewProtect)`**

Changes the protection constants on a region of virtual memory (e.g., to make read-only memory writable).

* **Address:** (`Pointer`) The starting address of the memory region.
* **Size:** (`number`) The size of the region in bytes.
* **NewProtect:** (`number`) The new memory protection constant (e.g., `0x40` for `PAGE_EXECUTE_READWRITE`). You will need to know these constants.
