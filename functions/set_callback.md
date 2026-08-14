# set\_callback

Function that sets callback to be dispatched by the client threads.

Only one callback can be set per callback type.

For all available callbacks see:

[Callbacks](https://app.gitbook.com/s/v5ydQ1YxN5w1i7hiOluk/callbacks "mention")



```luau
set_callback(name: string, callback: function | nil)
```



**Example:**

```lua
local function on_draw()
    draw.circle(100, 100, 10, 0xFFFFFFFF)
end

set_callback("draw", on_draw)
```
