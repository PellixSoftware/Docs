# set\_callback

Function that sets callback to be dispatched by the client threads.

Only one callback can be set at once.

For all available callbacks see:

[Broken link](/broken/pages/4U5LDDwJv7U9ujMLkRr4 "mention")



**Example:**

```lua
local function on_draw()
    draw.circle(100, 100, 10, 0xFFFFFFFF)
end

set_callback("draw", on_draw)
```
