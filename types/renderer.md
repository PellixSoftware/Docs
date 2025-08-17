---
description: >-
  The Renderer is a global object used to perform all drawing operations. You do
  not create an instance of it; instead, you call its methods directly. It is
  typically available within a rendering event.
---

# Renderer

## Methods

#### **`Renderer:WorldToScreen(WorldPosition)`**

Projects a 3D coordinate from the game world onto the 2D screen space. This is essential for drawing UI elements that are attached to objects or players in the game.

* **WorldPosition:** (`Vector3`) The position in 3D world space.
* **Returns:** (`Vector2`) The corresponding 2D position on the screen. Returns vector of two NaN values if the position is not visible on the screen. (NaN vectors will be automatically ignored during any rendered call, silently failing.)

```lua
local PlayerPosition = Vector3.new(1500, 2500, 100)
local ScreenPosition = Renderer:WorldToScreen(PlayerPosition)

if ScreenPosition then
    -- Draw something at the player's screen position
    Renderer:DrawText("Player", ScreenPosition, Color.new(255, 255, 255))
    -- Explicitly check if the point is out of screen
    if ScreenPosition.x ~= ScreenPosition.x or ScreenPosition.y ~= ScreenPosition.y then
        print("Out of screen!")
    end
end
```

**`Renderer:CalcTextSize(Text)`**

Calculates the width and height of a string of text before drawing it. This is useful for aligning text or drawing a background box behind it.

* **Text:** (`string`) The text to measure.
* **Returns:** (`Vector2`) A vector where `x` is the width and `y` is the height of the text.

```lua
local MyText = "Hello, World!"
local TextSize = Renderer:CalcTextSize(MyText)

print("Width: " .. TextSize.x .. ", Height: " .. TextSize.y)
```

**`Renderer:DrawLine(From, To, Color, Thickness)`**

Draws a straight line between two points.

* **From:** (`Vector2`) The starting screen coordinate.
* **To:** (`Vector2`) The ending screen coordinate.
* **Color:** (`Color`) The color of the line.
* **Thickness:** (`number`) The thickness of the line in pixels.

**`Renderer:DrawRect(From, To, Color, Rounding, Thickness)`**

Draws the outline of a rectangle.

* **From:** (`Vector2`) The top-left corner of the rectangle.
* **To:** (`Vector2`) The bottom-right corner of the rectangle.
* **Color:** (`Color`) The color of the border.
* **Rounding:** (`number`) The radius for the corners. A value of `0` results in sharp corners.
* **Thickness:** (`number`) The thickness of the border in pixels.

**`Renderer:DrawRectFilled(From, To, Color, Rounding)`**

Draws a solid, filled rectangle.

* **From:** (`Vector2`) The top-left corner of the rectangle.
* **To:** (`Vector2`) The bottom-right corner of the rectangle.
* **Color:** (`Color`) The fill color.
* **Rounding:** (`number`) The radius for the corners.

**`Renderer:DrawCircle(Pos, Radius, Segments, Color, Thickness)`**

Draws the outline of a circle.

* **Pos:** (`Vector2`) The center position of the circle.
* **Radius:** (`number`) The radius of the circle in pixels.
* **Segments:** (`number`) The number of segments to use to draw the circle. More segments result in a smoother circle. A value of 0 will result in extra code execution to calculate best-ish value.
* **Color:** (`Color`) The color of the outline.
* **Thickness:** (`number`) The thickness of the outline in pixels.

**`Renderer:DrawCircleFilled(Pos, Radius, Segments, Color)`**

Draws a solid, filled circle.

* **Pos:** (`Vector2`) The center position of the circle.
* **Radius:** (`number`) The radius of the circle in pixels.
* **Segments:** (`number`) The number of segments for the circle's shape.
* **Color:** (`Color`) The fill color of the circle.

**`Renderer:DrawText(Text, Pos, Color)`**

Draws text on the screen.

* **Text:** (`string`) The text to be displayed.
* **Pos:** (`Vector2`) The screen position for the top-left of the text.
* **Color:** (`Color`) The color of the text.

## Example Usage

Here is an example showing how to combine some of these functions to draw a health bar with a name above it.

```lua
-- Assume this code runs inside a rendering callback

local ScreenPosition = Vector2.new(200, 300)
local BarSize = Vector2.new(100, 10)
local BarBackgroundColor = Color.new(50, 50, 50)
local BarForegroundColor = Color.new(0, 255, 0) -- Green for health

-- Calculate the bottom-right corner of the bar
local BarEndPosition = ScreenPosition + BarSize

-- 1. Draw the background of the health bar (dark grey)
Renderer:DrawRectFilled(ScreenPosition, BarEndPosition, BarBackgroundColor, 2.0)

-- 2. Draw the foreground (the actual health)
-- For this example, we'll assume 75% health
local HealthPercentage = 0.75
local HealthBarEndPosition = Vector2.new(ScreenPosition.x + (BarSize.x * HealthPercentage), ScreenPosition.y + BarSize.y)
Renderer:DrawRectFilled(ScreenPosition, HealthBarEndPosition, BarForegroundColor, 2.0)

-- 3. Draw a border around the bar
Renderer:DrawRect(ScreenPosition, BarEndPosition, Color.new(0, 0, 0), 2.0, 1.0)

-- 4. Draw a name centered above the health bar
local PlayerName = "Player1"
local TextSize = Renderer:CalcTextSize(PlayerName)
local TextPosition = Vector2.new(ScreenPosition.x + (BarSize.x / 2) - (TextSize.x / 2), ScreenPosition.y - TextSize.y - 2)
Renderer:DrawText(PlayerName, TextPosition, Color.new(255, 255, 255))
```
