---
description: Allows to access global variables.
icon: globe
---

# globals



```luau
globals.curtime(): number
```

Returns current game time.



```luau
globals.tick_count(): number
```

Returns current number of ticks in the game.



{% code overflow="wrap" %}
```luau
globals.frame_count(): number
```
{% endcode %}

Returns current frame number in the game.



:warning: `curtime()` and `tick_count()` are not available in the draw callback.



```luau
globals.network_game_client(): uintptr_t
```

Returns address of the network game client structure.



```luau
globals.local_player_controller(): uintptr_t
```

Returns address to the pointer of the local player controller.



```luau
globals.short_map_name(): string
```

Returns current map name. For example: `de_mirage`



{% code overflow="wrap" %}
```luau
globals.system_tick_count(): number
```
{% endcode %}

Returns current system tick count (equivalent of winapi GetTickCount64)

