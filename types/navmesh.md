---
description: Type that represents a loaded navigation mesh.
icon: map-location-dot
---

# navmesh

{% code overflow="wrap" %}
```luau
navmesh.areas: navarea_list
```
{% endcode %}

Navigation area list which supports index and length operations.



{% code overflow="wrap" %}
```luau
navmesh.ladders: navladder_list
```
{% endcode %}

Navigation area ladder list which supports index and length operations.



{% code overflow="wrap" %}
```luau
navmesh:find_nearest_area(x: number, y: number, z: number): navarea | nil
```
{% endcode %}

Finds nearest area to the point.



{% code overflow="wrap" %}
```luau
navmesh:find_path_by_points(x0: number, y0: number, z0: number, x1: number, y1: number, z1: number [, callback: (from: navarea, to: navarea): number | nil = nil, allow_ladders = false]): array<navarea | navladder> | nil
```
{% endcode %}

Finds path using Dijkstra algorithm with priority queue. If callback is specified it should return cost (usually distance between the areas) or nil if point must be skipped.

`allow_laders` allows to include ladders into the path finding. You can differentiate between `navarea` and `navladder` with `area.is_ladder`.



{% code overflow="wrap" %}
```luau
navmesh:find_path(from: navarea, to: navarea [, callback: (from: navarea, to: navarea): number | nil = nil, allow_ladders = false]): array<navarea | navladder> | nil
```
{% endcode %}

Same as `find_path_by_points` but accepts areas instead.

