---
description: Access to in-game items and weapons.
icon: gun
---

# itemsystem

**weapon\_info**:

{% code overflow="wrap" %}
```luau
class_name: string -- Weapon class name like weapon_deagle
--[[
Weapon type index
0 - pistol
1 - rifle
2 - sniperrifle
3 - machinegun
4 - smg
5 - shotgun
6 - equipement
7 - grenade
8 - melee
9 - unknown
]]
type_index: number
class_name_hash: uint64_t -- make_hash compatible class name hash
localized_name: string | nil -- Localized weapon name like "AWP"
```
{% endcode %}



{% code overflow="wrap" %}
```luau
itemsystem.find_weapon_by_index(index: number): weapon_info
```
{% endcode %}

Retrieves weapon info by item definition index.

