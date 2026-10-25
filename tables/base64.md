---
description: Base64 encode/decode primitives.
icon: table-pivot
---

# base64

{% code overflow="wrap" %}
```luau
base64.encode(data: string): string
```
{% endcode %}

Encode string as base64.



{% code overflow="wrap" %}
```luau
base64.decode(data: string): string
```
{% endcode %}

Decode base64 encoded string.\
Assumes that input is always valid, stops early otherwise.
