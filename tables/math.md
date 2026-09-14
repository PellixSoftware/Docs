---
description: Extensions to the base lua math table.
icon: calculator
---

# math

{% code overflow="wrap" %}
```luau
math.normalize_yaw(yaw: number): number
```
{% endcode %}

Normalize yaw to be in the 180 to -180 range.



{% code overflow="wrap" %}
```luau
math.angle_to(x0: number, y0: number, z0: number, x1: number, y1: number z1: number): pitch: number, yaw: number, roll: number
```
{% endcode %}

Calculate angle between two 3D points. Clamps pitch to the +-89 range.



{% code overflow="wrap" %}
```luau
math.angle_forward(pitch: number, yaw: number, roll: number): pitch: number, yaw: number, roll: number
```
{% endcode %}

Calculate normalized forward direction relative to the angle.



{% code overflow="wrap" %}
```luau
math.angle_right(pitch: number, yaw: number, roll: number): pitch: number, yaw: number, roll: number
```
{% endcode %}

Calculate normalized right direction relative to the angle.



{% code overflow="wrap" %}
```luau
math.angle_up(pitch: number, yaw: number, roll: number): pitch: number, yaw: number, roll: number
```
{% endcode %}

Calculate normalized up direction relative to the angle.

