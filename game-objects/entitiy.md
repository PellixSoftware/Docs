---
description: The Entity is the most basic object in the game world.
---

# Entitiy

{% hint style="info" %}
Prefer using entity object over raw read calls. This is for one simple reason: when you create an entity over an address you've recieved from another, cheat will automatically find its class name and size and cache that for you. The only case using read might be beneficial is when you need one exact value by the offset.
{% endhint %}

## Constructing

You can easily construct an entity from a Pointer for automatic caching and read optimization like this:

```lua
EntityPointer = 0x7FFABDCDEFAB
EntityClass = Entity.new(EntityPointer)
```

## Methods

**`entity:GetBase()`**

Returns the base memory address of the entity.

* **Returns:** (`Pointer`) A `Pointer` object to the entity's base address.

**`entity:GetHealth()` / `entity:GetMaxHealth()`**

Gets the current or maximum health of the entity.

* **Returns:** (`number`) The health value.

**`entity:GetOrigin()` / `entity:GetRotation()` / `entity:GetVelocity()`**

Gets the entity's position, rotation (as Euler angles), or current velocity.

* **Returns:** (`Vector3`) A vector representing the requested value.

**`entity:IsAlive()`**

Checks if the entity is currently alive.

* **Returns:** (`boolean`) `true` if the entity's `LifeState` is `0`.

**`entity:GetLifeState()`**

Gets the current life state of the entity (e.g., alive, dying, dead).

* **Returns:** (`char`) The life state value. `0` typically means alive.

**`entity:GetIndex()`**

Gets the unique index of the entity in the game's entity list.

* **Returns:** (`number`) The entity index.

**`entity:GetIdentity()`**

Gets a pointer to the entity's identity information structure.

* **Returns:** (`Pointer`)

**`entity:GetBBox()`**

Gets the entity's bounding box used for collision detection.

* **Returns:** (`BBox3D` user-data)
