---
description: Allows to create custom UI elements and access UI state.
icon: display
---

# ui

```lua
ui.get_mouse_pos(): x: number, y: number | nil
```

Get mouse position on the overlay. For two pc setup (e.g. DMA) returns mouse position on the second PC. Returns nil if mouse is not on the overlay.

Can be called only from the draw callback.



#### **Getters/setters:**

{% code overflow="wrap" %}
```lua
ui.set(ref: number, value: boolean | number): boolean | number | nil
```
{% endcode %}

Sets value of the custom UI element. Returns old value.



{% code overflow="wrap" %}
```lua
ui.get(ref: number): boolean | number | nil
```
{% endcode %}

Retrieves value of the custom UI element.



#### **Custom elements:**

```lua
ui.new_text(text: string [, color: number, hidden: boolean]): number
```

Creates new UI text element.



```lua
ui.new_button(text: string [, callback: function, hidden: boolean]): number
```

Creates new UI button element.



```lua
ui.new_checkbox(text: string [, callback: function(v: boolean), hidden: boolean]): number
```

Creates a new UI checkbox element.



{% code overflow="wrap" %}
```lua
ui.new_slider_int(text: string, default_value: number, min: number, max: number [, callback: function(v: number), hidden: boolean])
```
{% endcode %}

Creates a new UI integer slider element.



{% code overflow="wrap" %}
```lua
ui.new_slider_float(text: string, default_value: number, min: number, max: number [, display_precision: number, callback: function(v: number), hidden: boolean])
```
{% endcode %}

Creates a new UI integer slider element. Set display\_precision to 0 to match behavior of the printf %g specification.



