---
description: >-
  This page contains information about performance tips and tricks that you can
  use in your code to improve overall performance of your Lua script.
---

# Performance guidelines

In our Lua API we expose our API functions in the following format:

<pre class="language-lua"><code class="lang-lua"><strong>_G[group] = table
</strong></code></pre>

\_G is a global table which you index every time when you use your call to our API.

If you cache API function that you want to use locally in your script it will prevent Lua from indexing global table for the group, then indexing group table for the table entry, which is a slower operation than local variable access.

This can be done like this:

```lua
local draw_line = draw.line
draw_line(...)
```

