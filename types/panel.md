---
description: Type that represents panorama CUIPanel.
icon: file-code
---

# panel

```luau
panel.base: uintptr_t
```

Panel base address.



{% code overflow="wrap" %}
```luau
panel.id: string | nil
```
{% endcode %}

Panel unique identifier string.



{% code overflow="wrap" %}
```luau
panel:get_absolute_pos(): x: number, y: number
```
{% endcode %}

Panel absolute position on the screen (please note that this is not accurate for panels with custom position/transform styles).



{% code overflow="wrap" %}
```luau
panel:get_size(): w: number, h: number
```
{% endcode %}

Panel on-screen size.



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

