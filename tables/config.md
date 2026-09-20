---
description: Interface to perform operations with a configuration file.
icon: page
---

# config

**Performance note:**&#x20;

Iterating through every configuration file entry is slow.

Do not retrieve config reference multiple times, save it in you script and reuse later if needed.&#x20;



**Functions:**

```luau
config.get_ref(id: string): number
```

Retrieves a reference to the configuration entry



```luau
config.get(ref: number): boolean | number | string | nil
```

Retrieves current configuration value by reference.



```luau
config.set(ref: number, value: boolean | number | string)
```

Sets the configuration value by reference.



{% code overflow="wrap" %}
```luau
config.new(name: string, value: boolean | number | string): number
```
{% endcode %}

Creates new script local configuration value or finds existing one and returns reference to it.

This entry persists across script reloads.
