---
description: Allows to access internal game structures offsets.
icon: sitemap
---

# schema

**Functions:**

{% code overflow="wrap" %}
```lua
schema.get([library_name: string = "client.dll", ] class_name: string, field_name: string): number
```
{% endcode %}

Returns schema class field offset in bytes. Library name specified in the following format: `libname.dll`

If library name is not specified, `client.dll` is used.



{% code overflow="wrap" %}
```lua
schema.get_class_size([library_name: string = "client.dll", ] class_name: string): number
```
{% endcode %}

Returns schema class size in bytes.
