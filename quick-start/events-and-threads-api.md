# Events & Threads API

The scripting engine is built on a multi-threaded event system. Instead of running a single script from top to bottom, you register functions (callbacks) to be executed when specific game events occur.

This system is designed for high performance and stability by processing different tasks in parallel.

#### Key Concepts

1. **Event Notifiers:** These are global objects (like `OnPlayer`, `OnRenderFrame`, etc.) that you use to "subscribe" to game events. You register a function, and the engine will automatically call it at the right time.
2. **Threaded Sandboxing:** Each category of events runs in its own separate, sandboxed Lua environment. That means **you cannot share** your variables normally, but it allows you to run threads in parallel.
   * The `OnLocalPlayer` event runs in the "LocalPlayer" thread.
   * The `OnPrePlayers`, `OnPlayer`, and `OnPostPlayers` events all share the "Players" thread.
   * The `OnPreEntities`, `OnEntity`, and `OnPostEntities` events all share the "Entities" thread.
   * The `OnRenderFrame` event runs in the "Render" thread.
3. **Data Sharing with Global Storage (`G`)**: Because each thread is sandboxed, even a global variable created in one event (like `OnPlayer`) is **not** accessible in another (like `OnRenderFrame`). To share data between threads, you must use the special global storage table, available as `G`. This table is accessible from all threads and is the primary way to pass information from game logic to your rendering logic.&#x20;

{% hint style="info" %}
Global storage can **only** hold tables of values, not values directly. This is done intentionally to encourage you to limit your usage of it to copying your own tables with values to it, minimizing the time of access. Each adding of new table to `G` will block other threads trying to access it at the same time, and each `G.MyTable` will lock each thread acessing `G.MyTable`&#x20;
{% endhint %}

***

## Event Notifiers

These are the global objects you use to register your callback functions.

#### `Notifier:RegisterCallback(function)`

This is the only method you will use on a notifier object. It takes one argument: the function you want to be called when the event occurs.

**Syntax:**

```lua
-- The name of the notifier determines when this function is called.
OnPlayer:RegisterCallback(function(Controller, Pawn)
    -- This code will run for every player in the game.
    if Pawn:IsAlive() then
        print(Controller:GetName() .. " is alive.")
    end
end)
```

## Available Events

### **Local Player Logic**

* **`OnLocalPlayer`**: Runs once per tick, specifically for the local player. This is the ideal place for logic that only affects your own character.
  * **Thread:** LocalPlayer
  * **Callback Arguments:** `(Controller, Pawn)`
    * `Controller`: (`PlayerController`) The local player's controller.
    * `Pawn`: (`PlayerPawn`) The local player's pawn.

### **Player Iteration Loop**

This set of events fires in sequence for every player on the server, allowing you to run code before, during, and after iterating through all players.

* **`OnPrePlayers`**: Runs **once** per tick, before the loop through players begins. Ideal for initializing data for the current tick.
  * **Thread:** Players
  * **Callback Arguments:** None.
* **`OnPlayer`**: Runs **for each player** in the game, one by one. This is where you will perform logic on individual players.
  * **Thread:** Players
  * **Callback Arguments:** `(Controller, Pawn)`
    * `Controller`: (`PlayerController`) The current player's controller in the loop.
    * `Pawn`: (`PlayerPawn`) The current player's pawn.
* **`OnPostPlayers`**: Runs **once** per tick, after the loop through all players has finished. Ideal for cleanup or for moving collected data to the global storage (`G`).
  * **Thread:** Players
  * **Callback Arguments:** None.

### **Entity Iteration Loop**

This loop is similar to the player loop but runs for every entity in the game.

* **`OnPreEntities`**: Runs **once** per tick, before the entity loop begins.
  * **Thread:** Entities
  * **Callback Arguments:** None.
* **`OnEntity`**: Runs **for each entity** in the game.
  * **Thread:** Entities
  * **Callback Arguments:** `(Entity, NameHash, ClassHash)`
    * `Entity`: (`Entity`) The current entity object.
    * `NameHash`: (`number`) A hashed value of the entity's name.
    * `ClassHash`: (`number`) A hashed value of the entity's class name.
* **`OnPostEntities`**: Runs **once** per tick, after the entity loop has finished.
  * **Thread:** Entities
  * **Callback Arguments:** None.

### **Rendering**

* **`OnRenderFrame`**: Runs on every single frame that is rendered. This is where all drawing logic should go. To avoid impacting performance, game logic should be done in other events.
  * **Thread:** Render
  * **Callback Arguments:** `(Renderer)`
    * `Renderer`: (`Renderer`) The global renderer object used for all drawing functions.

***

#### Full Example: ESP (Enemy Location Drawing)

This example demonstrates the complete workflow: gathering data in the `Players` thread, passing it to the `Render` thread via the `G` storage table, and then drawing it on the screen.

```lua
-- This script will draw a white circle at the feet of every player.

-- 1. Use the 'OnPrePlayers' event to initialize an empty table for this tick.
-- This runs in the 'Players' thread.
OnPrePlayers:RegisterCallback(function()
	-- 'PlayerData' is a local variable, only visible within this thread.
	PlayerData = {}
end)

-- 2. Use the 'OnPlayer' event to loop through all players and collect their positions.
-- This also runs in the 'Players' thread.
OnPlayer:RegisterCallback(function(Controller, Pawn)
	-- Check if the pawn is valid and alive before storing its data.
	if Pawn and Pawn:IsAlive() then
		table.insert(PlayerData, Pawn:GetOrigin())
	end
end)

-- 3. Use 'OnPostPlayers' after the loop is finished to move the collected data
--    into the shared global storage 'G'. This makes it accessible to other threads.
OnPostPlayers:RegisterCallback(function()
	G.PlayerPositions = PlayerData
end)

-- 4. Finally, use 'OnRenderFrame' to draw the visuals.
-- This runs in the separate 'Render' thread.
OnRenderFrame:RegisterCallback(function(Renderer) 
	-- Check if our data exists in the global storage.
	if not G.PlayerPositions then return end

	-- Retrieve the table that was placed in 'G' by the 'Players' thread.
	local PositionsToDraw = G.PlayerPositions

	-- Loop through the positions and draw a circle for each one.
	for _, Position3D in pairs(PositionsToDraw) do
		-- Project the 3D world position to a 2D screen coordinate.
		local ScreenPosition = Renderer:WorldToScreen(Position3D)

		-- Only draw if the position is visible on the screen.
		if ScreenPosition then
			local CircleColor = Color.new(1.0, 1.0, 1.0, 1.0) -- White
			Renderer:DrawCircleFilled(ScreenPosition, 5, 12, CircleColor)
		end
	end
end)
```
