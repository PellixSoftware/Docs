---
description: >-
  The Pointer object is used for low-level memory operations. It's mostly
  compatible with Lua numbers, but contains 64 bit unsigned integer.
---

# Pointer

{% hint style="info" %}
Lua language uses 64 bit floating points as numbers, which isn't always sufficient in context of memory hacking, hence pointer type.
{% endhint %}

{% hint style="info" %}
All pointer operations are **non-mutating**. Performing an operation on a pointer will always return a **new** `Pointer` object and will not modify the original one.
{% endhint %}

## Constructors

**`Pointer.new()`**

Creates a new `Pointer` object with its address initialized to `0` (a null pointer).

* **Returns:** (`Pointer`) A new null pointer.

```lua
local NullPointer = Pointer.new()
```

**`Pointer.new(address)`**

Creates a new `Pointer` object pointing to the specified memory address.

* **address:** (`number`) The memory address to point to.

Return&#x73;**:** (`Pointer`) A new pointer object.

```lua
-- Create a pointer to a specific base address
local BaseAddress = 0x140000000
local ModuleBase = Pointer.new(BaseAddress)
```

## Operators

`Pointer` objects support addition and subtraction operators to calculate new memory addresses.

**Addition (`+`)**

Used to add a numerical offset to a pointer's address, resulting in a new pointer. You can also add the address of another pointer.

* `Pointer + number`: Adds an offset to the pointer's address.
* `Pointer + Pointer`: Adds the address of the second pointer to the address of the first.

```lua
local BasePointer = Pointer.new(0x1000)

-- Add an offset to get to a specific member in a structure
local OffsetPointer = BasePointer + 0x48 -- Result is a new Pointer at 0x1048

-- The original BasePointer remains unchanged
-- print(BasePointer) --> still points to 0x1000

local OtherPointer = Pointer.new(0x200)
local CombinedPointer = BasePointer + OtherPointer -- Result is a new Pointer at 0x1200
```

**Subtraction (`-`)**

Used to subtract a numerical offset from a pointer's address. You can also subtract the address of another pointer.

* `Pointer - number`: Subtracts an offset from the pointer's address.
* `Pointer - Pointer`: Subtracts the address of the second pointer from the address of the first, creating a new pointer from the resulting value.

```lua
local DataPointer = Pointer.new(0x2050)

-- Subtract an offset
local HeaderPointer = DataPointer - 0x50 -- Result is a new Pointer at 0x2000

local StartPointer = Pointer.new(0x3000)
local EndPointer = Pointer.new(0x3010)

-- This calculates the difference (16) and creates a new pointer at that address.
-- This is a less common operation than finding the distance.
local DifferencePointer = EndPointer - StartPointer -- Result is a new Pointer at 0x10
```
