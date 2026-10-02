---
description: Allows to access VPK format.
icon: box-isometric
---

# vpk

{% code overflow="wrap" %}
```luau
vpk.parse_binary_kv3(data: string): vpk_key_values
```
{% endcode %}

Parses binary KV3 format.



{% code overflow="wrap" %}
```luau
vpk.parse_resource(data: string, callback: function(signature: number, offset: number, size: number, index: number, data: string): boolean): boolean
```
{% endcode %}

Parses VPK compiled resource format, executes callback for each block.\
Signature is a 4-byte value, for example (0x41544144 -> "DATA", 0x32444552 -> "RED2").\
Return false from the callback to stop iteration.



{% code overflow="wrap" %}
```luau
vpk.parse_texture(data: string): vpk_texture
```
{% endcode %}

Parses compiled VPK texture format (.vtex\_c).



{% code overflow="wrap" %}
```luau
vpk.parse_svg(data: string): string | nil
```
{% endcode %}

Parses compiled VPK SVG format (.vsvg\_c).



{% code overflow="wrap" %}
```luau
vpk.read_file(path: string): string | nil
```
{% endcode %}

Reads raw file from main VPK by path (including postfix like \_c).



