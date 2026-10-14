---
description: Allows to access internal panorama UI state.
icon: panorama
---

# panorama

```lua
panorama.find_hud_element(name: string): uintptr_t | nil
```

Find panorama hud element's base address by it's name (not a ui panel address but a hud object address).



```lua
panorama.list_hud_elements(): table<string, uintptr_t>
```

List panorama hud element names and their object addresses.



```lua
panorama.get_global_popups_address() : uintptr_t | nil 
```

Get address of the global popups. Contains popups which block all input behind them (match accept, premier map selection). Not a ui panel, `CCSGO_GlobalPopups` , ui panel is at +0x8.



{% code overflow="wrap" %}
```luau
 panorama.get_hud_address() : uintptr_t | nil 
```
{% endcode %}

Get address of the game hud object (not a ui panel, `CCSGO_Hud` , ui panel is at +0x8).



{% code overflow="wrap" %}
```luau
panorama.get_main_menu_address() : uintptr_t | nil 
```
{% endcode %}

Get address of the main menu object (not a ui panel, `CCSGO_MainMenu` , ui panel is at +0x8).



{% code overflow="wrap" %}
```luau
panorama.get_panel(address: uintptr_t | integer): panel
```
{% endcode %}

Get panel object by address. The input address is not checked (so you can pass arbitary panel addresses).
