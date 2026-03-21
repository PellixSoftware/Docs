---
description: >-
  Interface to draw on the screen. Almost every function can be called only from
  the draw callback.
icon: paintbrush
---

# draw

**Notes:**

Colors are specified in the RGBA format (0xAABBGGRR).

All functions can be called only from the \`on\_draw\` callback.



**Functions:**

{% code overflow="wrap" %}
```lua
draw.line((x0: number, y0: number) | (pos0: vector<2>), (x1: number, y1: number) | (pos1: vector<2>), color: number[, thickness: number])
```
{% endcode %}

Draws a line.



{% code overflow="wrap" %}
```lua
draw.rect((x0: number, y0: number) | (pos0: vector<2>), (x1: number, y1: number) | (pos1: vector<2>), color: number[, filled: boolean = false, rounding: number = 0.0, thickness: number = 1.0])
```
{% endcode %}

Draws a rectangle, thickness has no effect when filled == true.



{% code overflow="wrap" %}
```lua
draw.circle((x: number, y: number) | (pos: vector<2>), radius: number, color: number[, filled: boolean = false, num_segments: number = 0, thickness = 1.0])
```
{% endcode %}

Draws a circle, thickness has no effect when filled == true, `num_segments` selects count automatically if set to 0.



{% code overflow="wrap" %}
```lua
draw.polyline(points: table< { [1] = x, [2] = y } | x, y... >, color: number [, closed: boolean = false, thickness: number = 1.0 ])

draw.convex_poly_filled(points: table< { [1] = x, [2] = y } | x, y... >, color: number [, closed: boolean = false, thickness: number = 1.0 ])

-- Example
draw.polyline({
	5, 5, -- { 5, 5 }
	50, 10, -- { 50, 10 }
	50, 50, -- { 50, 50 }
	5, 50 -- { 5, 50 }
}, 0xffffffff, true)
```
{% endcode %}

Draws a polyline. `convex_poly_filled` draws filled convex polygon.\
Accepts array of 2-dimensional vectors or a repeated x,y sequence as numbers



{% code overflow="wrap" %}
```lua
draw.text(x: number, y: number, text: string, color: number [, align_x: number = 0.0, align_y: number = 0.0])
```
{% endcode %}

Draws a text starting at point (x, y) adjusted with (x, y) -= (size\_x, size\_y) \* (align\_x, align\_y).



{% code overflow="wrap" %}
```lua
draw.text_outline(x: number, y: number, text: string, color: number [, outline_color: number = 0x000000ff, align_x: number = 0.0, align_y: number = 0.0])
```
{% endcode %}

Draws a text with outline starting at point (x, y) adjusted with (x, y) -= (size\_x, size\_y) \* (align\_x, align\_y).



```lua
draw.text_size(text: string)
```

Calculates text size in pixels.



```lua
draw.overlay_size(): number, number
```

Returns size of the overlay window in pixels.



```lua
draw.render_size(): number, number
```

Returns screen size which game is using for rendering.



{% code overflow="wrap" %}
```lua
draw.world_to_screen((x: number, y: number, z: number) | pos: vector<3>): (number, number) | nil
```
{% endcode %}

Converts world space coordinates to the screen space coordinates, if object is too far away returns nil.



```lua
draw.load_texture_from_memory(data: string): texture, width: number, height: number | nil
```

Loads texture from memory directory (.png or .jpg)



{% code overflow="wrap" %}
```lua
draw.load_raw_texture_from_memory(data: string, width: number, height: number): texture | nil
```
{% endcode %}

Loads raw texture from 32-bit RGBA image in `data` (0xAABBGGRR)



{% code overflow="wrap" %}
```lua
draw.load_texture_from_file(filename: string): texture, width, height | nil
```
{% endcode %}

Loads texture from `C:\pWEBSITE_USERNAME\Scripts\Textures\*` if `Allow Unsafe` is enabled, an absolute path can be passed.



{% code overflow="wrap" %}
```lua
draw.texture(texture: texture, x0: number, y0: number, x1: number, y1: number [ , uv0x: number = 0, uv0y: number = 0, uv1x: number = 1, uv1y: number = 1, color: number = rgba(255, 255, 255, 255)])
```
{% endcode %}

Draws texture at specified coordinates.

