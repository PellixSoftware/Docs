---
description: Type that represents ladder in a mesh.
---

# 🪜 navladder

{% code overflow="wrap" %}
```luau
navladder:get_top(): x: number, y: number, z: number
```
{% endcode %}

Retrieves top ladder point.



{% code overflow="wrap" %}
```luau
navladder:get_bottom(): x: number, y: number, z: number
```
{% endcode %}

Retrieves bottom ladder point.



{% code overflow="wrap" %}
```luau
navladder.is_ladder: true
```
{% endcode %}

Always true, exists to differentiate between [navarea](navarea.md) and [navladder](navladder.md).



{% code overflow="wrap" %}
```luau
navladder.direction: number
```
{% endcode %}

Ladder direction, in 0-3 range, see `navladder.direction_name` for names.



{% code overflow="wrap" %}
```luau
navladder.direction_name: 'north'|'east'|'south'|'west'|'?'
```
{% endcode %}

Ladder direction name.



Connected area indexes:

{% code overflow="wrap" %}
```luau
navladder.top_forward_area_index: number | nil
navladder.top_left_area_index: number | nil
navladder.top_right_area_index: number | nil
navladder.top_behind_area_index: number | nil
navladder.bottom_area_index: number | nil
navladder.bottm_left_area_index: number | nil
navladder.bottm_right_area_index: number | nil
```
{% endcode %}
