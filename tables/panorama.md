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
panorama.list_hud_elements(): array<string>
```

List panorama hud element names.



```lua
panorama.get_global_popups_address() : uintptr_t | nil 
```

Get address of the global popups. Contains popups which block all input behind them (match accept, premier map selection).



