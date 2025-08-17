---
description: >-
  A Color object represents a 32-bit RGBA color. It is used in all Renderer
  drawing functions. All color components are represented as floating-point
  numbers between 0.0 (no intensity) and 1.0 (full int
---

# Color

## Constructors

**`Color.new()`**

Creates a new, default `Color` object. This is typically black with full alpha `(0.0, 0.0, 0.0, 1.0)`.

* **Returns:** (`Color`) A new `Color` object.

```lua
local DefaultColor = Color.new()
```

**`Color.new(r, g, b, a)`**

Creates a new `Color` object from the specified Red, Green, Blue, and Alpha components.

* **r:** (`number`) The red component (0.0-1.0).
* **g:** (`number`) The green component (0.0-1.0).
* **b:** (`number`) The blue component (0.0-1.0).
* **a:** (`number`, _optional_) The alpha (opacity) component (0.0-1.0). Defaults to `1.0`.
* **Returns:** (`Color`) A new `Color` object with the given component values.

```lua
-- Create a semi-transparent blue color
local TranslucentBlue = Color.new(0.0, 0.0, 1.0, 0.5)

-- Create a solid red color (alpha defaults to 1.0)
local SolidRed = Color.new(1.0, 0.0, 0.0)
```

## Properties

**`r`, `g`, `b`, `a`**

* (`number`) The individual RGBA components of the color, ranging from 0.0 to 1.0. These can be read from or assigned to.

```lua
local MyColor = Color.new(1.0, 0.0, 1.0) -- Magenta
print(MyColor.r) -- Outputs: 1.0

-- Make the color more greenish
MyColor.g = 0.6 -- (Represents 150/255)

-- Make it semi-transparent
MyColor.a = 0.8 -- (Represents 200/255)
```
