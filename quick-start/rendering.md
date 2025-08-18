---
description: >-
  The Renderer is a global object used to perform all drawing operations. You do
  not create an instance of it; instead, you call its methods directly from the
  callback.
---

# Rendering

## The Render Callback

All drawing operations must be performed inside a special function that is executed by the engine on every frame. This function is known as a "render callback".

To create one, you must register your function with the `OnFrameRender` event. This event will pass the `Renderer` object to your function as an argument, which you will then use to call all drawing functions.

#### Registration Syntax

```lua
OnFrameRender:RegisterCallback(function(Renderer)
    -- Your drawing code goes here.
    -- This function will be called every frame.
end)
```

#### Example

Here is a basic example that draws "Hello, World!" at a fixed position on the screen.

```lua
-- Register a function to be called on every frame render event
OnFrameRender:RegisterCallback(function(Renderer)
    -- Define the position and color for our text
    local textPosition = Vector2.new(100, 150)
    local textColor = Color.new(1, 1, 1) -- White

    -- Use the Renderer object passed to our function to draw the text
    Renderer:DrawText("Hello, World!", textPosition, textColor)
end)
```

## Utility Functions

These functions help with calculations needed for drawing, such as converting world coordinates to screen coordinates or measuring text size.

**`Renderer:WorldToScreen(WorldPosition)`**

Projects a 3D coordinate from the game world onto the 2D screen space. This is essential for drawing UI elements that are attached to objects or players in the game.

* **WorldPosition** (`Vector3`): The position in 3D world space.
* **Returns**: A `Vector2` with the corresponding 2D position on the screen. If the position is behind the camera or off-screen, it returns a vector with `NaN` (Not a Number) coordinates.

{% hint style="info" %}
Drawing functions will automatically and silently ignore calls that use `NaN` coordinates.
{% endhint %}

```lua
local playerPosition = Vector3.new(1500, 2500, 100)
local screenPosition = Renderer:WorldToScreen(playerPosition)

-- The check for nil is important as the function might not return anything
-- in some edge cases. The NaN check is more explicit for off-screen positions.
if screenPosition then
    -- Draw a label at the player's screen position
    Renderer:DrawText("Player", screenPosition, Color.new(255, 255, 255))
    
    -- To explicitly check if the point is off-screen, you can check for NaN
    if screenPosition.x ~= screenPosition.x then
        print("Player is off-screen!")
    end
end
```

**`Renderer:CalcTextSize(Text)`**

Calculates the pixel width and height of a string before it is drawn. This is very useful for centering text or drawing a background box that fits the text perfectly.

* **Text** (`string`): The text to measure.
* **Returns**: A `Vector2` where `x` is the width and `y` is the height of the text.

```lua
local myText = "Hello, World!"
local textSize = Renderer:CalcTextSize(myText)

print("Width: " .. textSize.x .. ", Height: " .. textSize.y)
```

***

## Drawing Functions

These functions are used to draw various primitives to the screen.

**`Renderer:DrawLine(From, To, Color, Thickness)`**

Draws a straight line between two points.

* **From** (`Vector2`): The starting screen coordinate.
* **To** (`Vector2`): The ending screen coordinate.
* **Color** (`Color`): The color of the line.
* **Thickness** (`number`): The thickness of the line in pixels.

**`Renderer:DrawRect(From, To, Color, Rounding, Thickness)`**

Draws the outline of a rectangle.

* **From** (`Vector2`): The top-left corner of the rectangle.
* **To** (`Vector2`): The bottom-right corner of the rectangle.
* **Color** (`Color`): The color of the border.
* **Rounding** (`number`): The radius for the corners. Use `0` for sharp corners.
* **Thickness** (`number`): The thickness of the border in pixels.

**`Renderer:DrawRectFilled(From, To, Color, Rounding)`**

Draws a solid, filled rectangle.

* **From** (`Vector2`): The top-left corner of the rectangle.
* **To** (`Vector2`): The bottom-right corner of the rectangle.
* **Color** (`Color`): The fill color.
* **Rounding** (`number`): The radius for the corners.

**`Renderer:DrawCircle(Pos, Radius, Segments, Color, Thickness)`**

Draws the outline of a circle.

* **Pos** (`Vector2`): The center position of the circle.
* **Radius** (`number`): The radius of the circle in pixels.
* **Segments** (`number`): The number of line segments to use to approximate the circle. More segments create a smoother circle. A value of `0` will automatically calculate a reasonable number.
* **Color** (`Color`): The color of the outline.
* **Thickness** (`number`): The thickness of the outline in pixels.

**`Renderer:DrawCircleFilled(Pos, Radius, Segments, Color)`**

Draws a solid, filled circle.

* **Pos** (`Vector2`): The center position of the circle.
* **Radius** (`number`): The radius of the circle in pixels.
* **Segments** (`number`): The number of segments for the circle's shape.
* **Color** (`Color`): The fill color of the circle.

**`Renderer:DrawText(Text, Pos, Color)`**

Draws text on the screen.

* **Text** (`string`): The text to be displayed.
* **Pos** (`Vector2`): The screen position for the top-left corner of the text.
* **Color** (`Color`): The color of the text.

***

## Combined Example

Here is an example showing how to combine some of these functions to draw a player's name and a health bar.

```lua
-- This function will be called every frame, allowing you to draw to the screen.
OnRenderFrame:RegisterCallback(function(Renderer)
    -- 1. Define properties for our health bar
    local barPosition = Vector2.new(50, 50)
    local barSize = Vector2.new(200, 20)
    local health = 0.60 -- Simulate 60% health

    local colorBackground = Color.new(1, 0, 0, 0.5)
    local colorForeground = Color.new(0, 1, 0, 1)
    local colorBorder = Color.new(0, 0, 0, 1)
    local colorText = Color.new(1, 1, 1, 1)

    -- 2. Calculate the end position of the bar's background
    local barEndPosition = barPosition + barSize

    -- 3. Draw the background of the bar (the empty part)
    Renderer:DrawRectFilled(barPosition, barEndPosition, colorBackground, 3.0)

    -- 4. Calculate the width of the foreground bar based on the health percentage
    local foregroundWidth = barSize.x * health
    local foregroundEndPosition = Vector2.new(barPosition.x + foregroundWidth, barPosition.y + barSize.y)

    -- 5. Draw the foreground (the actual health)
    Renderer:DrawRectFilled(barPosition, foregroundEndPosition, colorForeground, 3.0)

    -- 6. Draw a border around the entire bar
    Renderer:DrawRect(barPosition, barEndPosition, colorBorder, 3.0, 1.0)

    -- 7. Draw a text label on top of the bar
    local text = "Health: " .. string.format("%d%%", health * 100)
    local textSize = Renderer:CalcTextSize(text)
    
    -- Center the text inside the bar
    local textPosition = Vector2.new(
        barPosition.x + (barSize.x / 2) - (textSize.x / 2),
        barPosition.y + (barSize.y / 2) - (textSize.y / 2)
    )
    Renderer:DrawText(text, textPosition, colorText)
end)
```
