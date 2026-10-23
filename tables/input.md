---
description: Allows to simulate mouse/keyboard inputs.
icon: computer-mouse
---

# input

```luau
input.get_backend_name(): string
```

Retrieves input backend name.



<mark style="color:$warning;">**All functions below are only available if user enabled**</mark><mark style="color:$warning;">**&#x20;**</mark><mark style="color:$warning;">**`Inputs`**</mark><mark style="color:$warning;">**&#x20;**</mark><mark style="color:$warning;">**permission in the lua tab!**</mark>

Note: Because callbacks may be executed on the same tick it's highly recommended to check if tick and frame count were changed before submitting a new input.



{% code overflow="wrap" %}
```luau
input.move_mouse(x: number, y: number [, absolute: boolean = false])
```
{% endcode %}

Moves mouse using mouse input device. Set absolute to `true` if you want to move mouse in the absolute screen coordinates.



```luau
input.mouse_button(button: number, down: boolean)
```

Changes state of the mouse button. 0 - `left`, 1 - `right`, 2 - `middle`.



```luau
input.keyboard_button(button: number, down: boolean)
```

Changes state of the keyboard button. Accepts virtual key codes from https://learn.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes.



```luau
input.is_keyboard_key_pressed(button: number [, from_second: boolean = false]): boolean
```

Retrieves state of the keyboard key.



{% code overflow="wrap" %}
```luau
input.restore_wasd_state()
```
{% endcode %}

Restores state of WASD keyboard keys that were previously modified by `input.keyboard_button` to their physical state.



{% code overflow="wrap" %}
```luau
input.angle_to_mouse_move(pitch: number, yaw: number): x: number, y: number | nil
```
{% endcode %}

Converts angle delta to the equivalent mouse movement delta. Delta is `view_angles - target_angles`. Returns `nil` when inputs are not possible (e.g. menu is opened).
