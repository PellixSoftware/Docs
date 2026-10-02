---
description: An example how to load texture from VPK and draw it.
---

# Loading texture from VPK

{% code overflow="wrap" %}
```lua
local file = vpk.read_file("panorama/images/econ/status_icons/10yearcoin_png.vtex_c")
local texture = vpk.parse_texture(file)

print("format_index:", texture.format_index)
print("format:", texture.format)
print("width:", texture.width)
print("height:", texture.height)
print("mip_levels:", #texture.mip_levels)

local once = false
local draw_texture = nil

local function on_draw()
    if not once then
        draw_texture = draw.load_raw_texture_from_memory(texture.mip_levels[1], texture.width, texture.height)
        once = true
    end

    if not draw_texture then
        return
    end
    
    local x = 100
    local y = 100
    draw.texture(x, y, x + texture.width, y + texture.height)
end

set_callback("draw", on_draw)
```
{% endcode %}

