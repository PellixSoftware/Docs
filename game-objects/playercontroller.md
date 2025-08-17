---
description: >-
  The PlayerController represents the player's connection and state, acting as
  the "brain" for a PlayerPawn. It holds information like the player's name and
  score.
---

# PlayerController

## Constructors

**`PlayerController.new(Pointer)`**

Creates a new `PlayerController` object from a memory pointer.

* **Returns:** (`PlayerController`)

**`PlayerController.new(Entity)`**

Creates a new `PlayerController` object from a generic `Entity` object.

* **Returns:** (`PlayerController`)

## Methods

**`controller:GetBase()`**

Returns the base memory address of the player controller.

* **Returns:** (`Pointer`)

**`controller:GetPawn()`**

Gets the `PlayerPawn` (the in-game character) that this controller is currently controlling. This is the primary way to link a controller to its pawn.

* **Returns:** (`PlayerPawn`) The pawn object, or `nil` if the player is not spawned.

```lua
-- Assume PlayerController is a valid PlayerController object
local PlayerPawn = PlayerController:GetPawn()

if PlayerPawn and PlayerPawn:IsAlive() then
    local PlayerOrigin = PlayerPawn:GetOrigin()
    print("Player is at: " .. PlayerOrigin.x)
end
```

{% hint style="info" %}
Prefer using the pawn object you recieved in the callback instead of calling GetPawn() as the one inside of the callback already has all the memory cached and ready for use while initializing a new one will result in a memory read call.
{% endhint %}

**`controller:GetName()`**

Gets the player's name.

* **Returns:** (`string`)

**`controller:GetIndex()`**

Gets the unique index of the player controller.

* **Returns:** (`number`)

**`controller:GetRoundKills()`**

Gets the number of kills the player has scored in the current round.

* **Returns:** (`number`)

**`controller:GetTickBase()`**

Gets the simulation tick base for the player.

* **Returns:** (`number`)
