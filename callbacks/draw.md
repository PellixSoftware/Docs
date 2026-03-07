---
icon: paintbrush
---

# draw

Executes every time when overlay frame is about to render.&#x20;

This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

```lua
local function on_draw()
    draw.line(0, 0, 100, 100, 0xffffffff)
end

set_callback("draw", on_draw)
```
