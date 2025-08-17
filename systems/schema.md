---
description: >-
  The Schema is a global object that acts as a database for the game's internal
  data layout. It allows you to query for the memory offsets of class members
  and the total size of classes.
---

# Schema

{% hint style="info" %}
**For performance reasons you're advised to only retrieve required offsets once at the start of your script.**
{% endhint %}

## Methods

**`Schema:Get(Library, Class, Member)`**

Retrieves the memory offset of a specific member within a class from a given library (e.g., a DLL exposed to Schema system).

* **Library:** (`string`) The name of the library or module containing the class (e.g., `"client.dll"`).
* **Class:** (`string`) The name of the class or data structure.
* **Member:** (`string`) The name of the member variable whose offset you want to find.
* **Returns:** (`number`) The integer offset of the member in bytes, or `0` if not found.

```lua
-- Get the offset for the health member in the C_BasePlayer class
local HealthOffset = Schema:Get("client.dll", "C_BasePlayer", "m_iHealth")

if HealthOffset > 0 then
    print("Health offset found at: " .. HealthOffset)
end
```

**`Schema:GetC(Class, Member)`**

A shorthand version of `Get` that searches within the primary client library. This is useful for accessing common game-related classes.

* **Class:** (`string`) The name of the class.
* **Member:** (`string`) The name of the member variable.
* **Returns:** (`number`) The integer offset of the member in bytes.

```lua
-- Same as the previous example, but shorter
local HealthOffset = Schema:GetC("C_BasePlayer", "m_iHealth")
```

**`Schema:GetClassSize(Library, Class)`**

Retrieves the total size of a class or structure in bytes from a specific library.

* **Library:** (`string`) The name of the library containing the class.
* **Class:** (`string`) The name of the class.
* **Returns:** (`number`) The total size of the class in bytes.

```lua
local PlayerClassSize = Schema:GetClassSize("client.dll", "C_BasePlayer")
print("C_BasePlayer size is: " .. PlayerClassSize .. " bytes")
```

**`Schema:GetClassSizeC(Class)`**

A shorthand version of `GetClassSize` that retrieves the size of a class from the primary client library.

* **Class:** (`string`) The name of the class.
* **Returns:** (`number`) The total size of the class in bytes.

```lua
local PlayerClassSize = Schema:GetClassSizeC("C_BasePlayer")
print("C_BasePlayer size is: " .. PlayerClassSize .. " bytes")
```
