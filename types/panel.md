---
description: Type that represents panorama CUIPanel.
icon: file-code
---

# panel

Note: `cached` parameter specifies whether specified attribute should be read directly from the memory or fetched from cache (which is faster), cache is updated about every 5 seconds.



```luau
panel.base: uintptr_t
```

Panel base address.



{% code overflow="wrap" %}
```luau
panel.id: string | nil
```
{% endcode %}

Panel unique identifier string. `nil` is returned if internal panel address is 0 (not if id is empty).



{% code overflow="wrap" %}
```luau
panel:get_absolute_pos([ cached: boolean = false ]): x: number, y: number
```
{% endcode %}

Panel absolute position on the screen (please note that this is not accurate for panels with custom position/transform styles).



{% code overflow="wrap" %}
```luau
panel:get_size([ cached: boolean = false ]): w: number, h: number
```
{% endcode %}

Panel on-screen size.



{% code overflow="wrap" %}
```luau
panel:find_child_by_id(cached: boolean, id: string...): panel | nil
```
{% endcode %}

Finds panorama panel child by following the id chain provided.



{% code overflow="wrap" %}
```luau
panel.children_count: number
```
{% endcode %}

Count of panel children.



{% code overflow="wrap" %}
```luau
panel.children: array<panel>
```
{% endcode %}

Children panel array.

