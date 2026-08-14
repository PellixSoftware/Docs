---
description: Allows to access internal panorama UI state.
icon: panorama
---

# panorama

```lua
panorama.find_hud_element(name: string): uintptr_t | nil
```

Find panorama hud element's base address by it's name.



```lua
panorama.list_hud_elements(): table<string, uintptr_t>
```

List panorama hud element names and their addresses.



```lua
panorama.get_global_popups_address() : uintptr_t | nil 
```

Get address of the global popups. Contains popups which block all input behind them (match accept, premier map selection).



{% code overflow="wrap" %}
```luau
 panorama.get_hud_address() : uintptr_t | nil 
```
{% endcode %}

Get address of the game hud object.



{% code overflow="wrap" %}
```luau
panorama.get_main_menu_address() : uintptr_t | nil 
```
{% endcode %}

Get address of the main menu object.
