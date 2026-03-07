---
icon: person
---

# player

Executes every time when basic player data was retrieved, player references in-game `CCSPlayerController`  and almost always has entire class cached into the memory.



```lua
pre_players()
player(player: entity)
post_players()
```



&#x20;This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

```lua
local teamnum_offset = schema.get("C_BaseEntity", "m_iTeamNum")

local player_teams = {}

local function on_pre_players()
    for i, v in next, player_teams 
        print(i, ": ", v)    
    end

    player_teams = {}
end

local function on_player(player)
    player_teams[player:get_index()] = player:get_int(teamnum_offset)
end

set_callback("pre_players", on_pre_players)
set_callback("player", on_player)
```
