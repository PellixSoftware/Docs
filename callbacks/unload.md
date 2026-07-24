---
icon: eject
---

# unload

Executes every time when script is about to be unloaded.



This callback can be registered by calling [set\_callback.md](../functions/set_callback.md "mention").



**Example:**

{% code overflow="wrap" %}
```luau
local function on_unload()
    -- save important data...
    print("unload!")
end

set_callback("unload", on_unload)
```
{% endcode %}

