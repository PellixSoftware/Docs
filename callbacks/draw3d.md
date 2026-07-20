---
icon: cube
---

# draw3d

Executes every time when overlay 3D frame is about to render.&#x20;

This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

```lua
local function on_draw3d()
	batcher:clear()
	batcher:add_aabb(0, 0, 0, 10, 10, 10)
	batcher:render()
end)

set_callback("draw3d", on_draw3d)
```

