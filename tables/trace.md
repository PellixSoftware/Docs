---
icon: eye
---

# trace

{% code overflow="wrap" %}
```luau
trace.visible(x0: number, y0: number, z0: number, x1: number, y1: number, z1: number): boolean
```
{% endcode %}

Check if two points are visible.



{% code overflow="wrap" %}
```luau
trace.distance(x0: number, y0: number, z0: 0, x1: number, y1: number, z1: number): number
```
{% endcode %}

Perform a ray tracing between two points and return distance on hit `>= 0.f` , returns negative value if points are visible to each other.

