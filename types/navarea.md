---
description: Type that represents navigation area in a mesh.
icon: square-dashed
---

# navarea

{% code overflow="wrap" %}
```luau
navarea:get_mins(): x: number, y: number, z: number
```
{% endcode %}

Retrieves min AABB area point.



{% code overflow="wrap" %}
```luau
navarea:get_maxs(): x: number, y: number, z: number
```
{% endcode %}

Retrieves max AABB area point.



{% code overflow="wrap" %}
```luau
navarea:get_center(): x: number, y: number, z: number
```
{% endcode %}

Retrieves area center point.



{% code overflow="wrap" %}
```luau
navarea:get_corner(index: number): x: number, y: number, z: number
```
{% endcode %}

Retrieves corner point by index.



{% code overflow="wrap" %}
```luau
navarea.corners_count: number
```
{% endcode %}

Amount of corners for this area. To be used with `navarea.get_corner`.



{% code overflow="wrap" %}
```luau
navarea:get_connection(index: number): area_id: number, edge_id: number
```
{% endcode %}

Retrieves nav connection info by index.



{% code overflow="wrap" %}
```luau
navarea.connections_count: number
```
{% endcode %}

Amount of connections for this area. To be used with `navarea.get_connection`.



{% code overflow="wrap" %}
```luau
navarea.get_closest_point_to(x: number, y: number, z: number): x: number, y: number, z: number
```
{% endcode %}

Retrieves closest point on the area to the specified 3D point.



{% code overflow="wrap" %}
```lua
navarea.is_ladder: false
```
{% endcode %}

Always false, exists to differentiate between [navarea](navarea.md) and [navladder](navladder.md).



{% code overflow="wrap" %}
```luau
navarea.is_crouch: boolean
```
{% endcode %}

If area requires crouch for traversal.



```luau
navarea.flags: number
```

Bitfield with raw navmesh flags.
