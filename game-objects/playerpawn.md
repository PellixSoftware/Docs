---
description: PlayerPawn object represents a player's physical character in the game world.
---

# PlayerPawn

## Constructors

**`PlayerPawn.new(Pointer)`**

Creates a new `PlayerPawn` object from a memory pointer.

* **Returns:** (`PlayerPawn`)

## Methods

{% hint style="info" %}
_(Includes all methods from the `Entity` class)_
{% endhint %}

**`pawn:GetActiveWeapon()`**

Gets the weapon the player is currently holding.

* **Returns:** (`WeaponBase`) An object representing the active weapon.

**`pawn:GetViewAngles()` / `pawn:GetEyeAngles()`**

Gets the player's current view angles (where they are aiming).

* **Returns:** (`Vector3`) A vector representing pitch, yaw, and roll.

**`pawn:GetViewOrigin()` / `pawn:GetShootPosition()`**

Gets the 3D position of the player's "eyes" or the position from where their bullets will originate.

* **Returns:** (`Vector3`)

**`pawn:GetArmor()`**

Gets the player's current armor value.

* **Returns:** (`number`) The armor value.

**`pawn:GetHasHelmet()`**

Checks if the player has a helmet.

* **Returns:** (`boolean`)

**`pawn:GetShotsFired()`**

Gets the number of shots fired in the current burst (recoils).

* **Returns:** (`number`)

**`pawn:GetAimPunch()`**

Gets the current view angle displacement caused by recoil.

* **Returns:** (`Vector3`)

**`pawn:IsScoped()`**

Checks if the player is currently zoomed in with a scoped weapon.

* **Returns:** (`boolean`) `true` if scoped.

**`pawn:IsDefusing()`**

Checks if the player is currently defusing the bomb.

* **Returns:** (`boolean`)

**`pawn:GetFlashAlpha()`**

Gets the current alpha level of the flashbang effect on the player's screen.

* **Returns:** (`number`) A value from 0.0 to 1.0.

**`pawn:GetCameraServices()` / `pawn:GetWeaponServices()` / etc.**

Gets a pointer to one of the player's "service" structures, which manage different aspects of the player's state.

* **Returns:** (`Pointer`)
