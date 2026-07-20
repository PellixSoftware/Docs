---
description: Allows to render 3D figures.
icon: cube
---

# draw3d

{% code overflow="wrap" %}
```luau
draw3d.create_batcher(): batcher3d
```
{% endcode %}

Creates a 3D batcher which is able to batch multiple triangles, AABBs and capsules for rendering in the 3D space.

`batcher3d` functions can only be called from `draw3d` callback.



{% code overflow="wrap" %}
```luau
draw3d.render_2d_texture(texture: texture, 
    x0: number, y0: number, z0: number, x1: number, y1: number, z1: number,
    x2: number, y2: number, z2: number, x3: number, y3: number, z3: number
)
```
{% endcode %}

Render 2D texture loaded by `draw.load_texture_from_*` functions in 3D space.



{% code overflow="wrap" %}
```luau
batcher3d:add_aabb(x0: number, y0: number, z0: number, x1: number, y1: number, z1: number)
```
{% endcode %}

Adds an axis aligned bounding box to the batcher.



{% code overflow="wrap" %}
```luau
batcher3d:add_capsule(x0: number, y0: number, z0: number, x1: number, y1: number, z1: number, radius: number)
```
{% endcode %}

Adds a capsule to the batcher.



{% code overflow="wrap" %}
```luau
batcher3d:render([color: number, wireframe: boolean = true])
```
{% endcode %}

Renders all batched triangles.



{% code overflow="wrap" %}
```luau
batcher3d:clear()
```
{% endcode %}

Resets batcher to the default state removing all batched triangles.

