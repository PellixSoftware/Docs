---
description: Interface to perform operations with a configuration file.
icon: page
---

# config

**Performance note:**&#x20;

Iterating through every configuration file entry is slow.

Do not retrieve config reference multiple times, save it in you script and reuse later if needed.&#x20;



**Functions:**

```lua
config.get_ref(id: string): number
```

Retrieves a reference to the configuration entry



```lua
config.get(ref: number): boolean | number
```

Retrieves current configuration value by reference.



```lua
config.set(ref: number, value: boolean | number)
```

Sets the configuration value by reference.
