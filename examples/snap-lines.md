# Snap lines

```lua
local origins = {}
local draw_origins = {}

local function on_pre_players()
    origins = {}
end

local function on_player(controller)
    local pawn = controller:get_pawn()
    if not pawn then
        return
    end
    
    origins[pawn:get_index()] = { pawn:get_abs_origin() }
end

local function on_post_players()
    draw_origins = origins
end

local function on_draw()
    local sx, sy = draw.overlay_size()
    for _, v in next, draw_origins do 
        local x, y = draw.world_to_screen(v[1], v[2], v[3])
        if not x then
            goto continue    
        end
        
        draw.line(sx * 0.5, sy, x, y, 0xffffffff)
        
        ::continue::
    end
end

set_callback("pre_players", on_pre_players)
set_callback("player", on_player)
set_callback("post_players", on_post_players)
set_callback("draw", on_draw)
```
