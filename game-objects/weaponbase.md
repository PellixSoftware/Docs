---
description: >-
  The WeaponBase object represents a weapon in the game. It contains information
  about its current state (clip ammo) and its static properties (damage, range,
  etc.).
---

# WeaponBase

## Methods

**`weapon:GetBase()`**

Returns the base memory address of the weapon.

* **Returns:** (`Pointer`) A `Pointer` object to the weapon's base address.

**`weapon:GetClip()` / `weapon:GetMaxClip()`**

Gets the current ammo count in the clip or the maximum ammo capacity of the clip.

* **Returns:** (`number`) The ammo count.

**`weapon:GetDamage()`**

Gets the base damage value for the weapon.

* **Returns:** (`number`) The damage value.

**`weapon:GetRange()` / `weapon:GetRangeModifier()`**

Gets the weapon's effective range and its range modifier.

* **Returns:** (`number`) The range value.

**`weapon:GetSpread()` / `weapon:GetAccuracyPenalty()`**

Gets the weapon's base spread or current accuracy penalty.

* **Returns:** (`number`) The inaccuracy value.

**`weapon:GetArmorRatio()` / `weapon:GetPenetrationModifier()`**

Gets the weapon's armor penetration values.

* **Returns:** (`number`)

**`weapon:GetItemDefinitionIndex()`**

Gets the unique ID that identifies the type of weapon (e.g., AK-47, Deagle).

* **Returns:** (`number`) The definition index.

**`weapon:IsReloading()`**

Checks if the weapon is currently in the process of reloading.

* **Returns:** (`boolean`) `true` if the weapon is reloading.
