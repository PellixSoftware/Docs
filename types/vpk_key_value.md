---
description: VPK key value type.
icon: cube
---

# vpk\_key\_value

{% code overflow="wrap" %}
```luau
vpk_key_value.get_type_name(): 'none'|'boolean'|'string'|'array'|'object'|'integer'|'float'|'other'
```
{% endcode %}

Retrieves value type name.



{% code overflow="wrap" %}
```luau
vpk_key_value.get_type_index(): number
```
{% endcode %}

Get internal VPK binary type index (see [here](https://github.com/ValveResourceFormat/ValveResourceFormat/blob/36f6a0fd6f6b5222aaf33cd80d40878a4a76e1d8/ValveResourceFormat/Resource/ResourceTypes/BinaryKV3.NodeType.cs#L5)).



{% code overflow="wrap" %}
```luau
vpk_key_value.get_orig_type_index(): number	
```
{% endcode %}

Same as `vpk_key_value.get_type_index()` but returns original type index.

Parser internally converts `ARRAY_TYPE*` to `ARRAY`, `*_AS_BYTE` and `*FALSE/ZERO/ONE` to their equivalents.



{% code overflow="wrap" %}
```luau
vpk_key_value:get([index: string | number]): vpk_key_value | boolean | number | string | nil
```
{% endcode %}

Retrieves value by index or key name.

If value is an object string is required.

If value is an array index is required starting with 1.



{% code overflow="wrap" %}
```luau
#vpk_key_value: number | nil
```
{% endcode %}

Retrieves size of the vpk key value of an object, an array or string, nil otherwise.

