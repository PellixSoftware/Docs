---
description: Allows to access global variables.
icon: globe
---

# globals

```lua
globals.curtime(): number
```

Returns current game time.



```lua
globals.tick_count(): number
```

Returns current number of ticks in the game.



:warning: `curtime()` and `tick_count()` are not available in the draw callback.



```lua
globals.network_game_client(): uintptr_t
```

Returns address of the network game client structure.



```lua
globals.local_player_controller(): uintptr_t
```

Returns address to the pointer of the local player controller.



```lua
globals.short_map_name(): string
```

Returns current map name. For example: `de_mirage`



