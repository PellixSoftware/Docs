---
description: Allows to simulate mouse/keyboard inputs.
icon: computer-mouse
---

# input

```lua
input.get_backend_name(): string
```

Retrieves input backend name. Possible values are: `kernelmode`, `usermode`, `makcu`, `kmboxnet` or `none`.

Please note that `usermode` exists internally for testing but it's not used in any of the release versions.



<mark style="color:$warning;">**All functions below are only available if user enabled**</mark><mark style="color:$warning;">**&#x20;**</mark><mark style="color:$warning;">**`Lua Allow Inputs`**</mark><mark style="color:$warning;">**&#x20;**</mark><mark style="color:$warning;">**in the global config!**</mark>



```lua
input.move_mouse(x: number, y: number [, absolute: boolean = false])
```

Moves mouse using mouse input device. Set absolute to `true` if you want to move mouse in the absolute screen coordinates.



```lua
input.mouse_button(button: number, down: boolean)
```

Changes state of the mouse button. 0 - `left`, 1 - `right`, 2 - `middle`.
