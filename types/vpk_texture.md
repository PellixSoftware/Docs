---
description: Type that represents VPK texture.
icon: image
---

# vpk\_texture

{% code overflow="wrap" %}
```luau
vpk_texture.format_index: number
```
{% endcode %}

Texture VPK format internal index (see [here](https://github.com/ValveResourceFormat/ValveResourceFormat/blob/36f6a0fd6f6b5222aaf33cd80d40878a4a76e1d8/ValveResourceFormat/Resource/ResourceTypes/Texture.cs#L257)).



{% code overflow="wrap" %}
```luau
vpk_texture.format: 'rgba8888' | 'bgra8888' | 'other'
```
{% endcode %}

Texture format name.



{% code overflow="wrap" %}
```luau
vpk_texture.width: number
vpk_texture.height: number
```
{% endcode %}

Texture width and height.



{% code overflow="wrap" %}
```luau
vpk_texture.mip_levels: array<string>
```
{% endcode %}

Texture mip levels with raw data.
