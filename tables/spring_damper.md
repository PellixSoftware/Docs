---
description: Spring damper smooth access.
icon: reel
---

# spring\_damper

Spring damper is a human-like smoothing algorithm with natural acceleration and velocity smoothing algorithm. You can use this algorithm to perform smooth human-like mouse movement.



{% code overflow="wrap" %}
```luau
spring_damper.new_state(): userdata
```
{% endcode %}

Creates a new spring damper state.



{% code overflow="wrap" %}
```luau
spring_damper.step(state: userdata, prev_pitch: number, prev_yaw: number, smooth_x: number, smooth_y: number [, max_aim_step: number = 0]): pitch: number, yaw: number
```
{% endcode %}

Performs a spring damper step, `prev_pitch` and `prev_yaw` are desired relative angle to the target.

If `max_aim_step` is <= 0 step is unlimited.



{% code overflow="wrap" %}
```luau
spring_damper.reset(state: userdata): userdata
```
{% endcode %}

Resets an internal spring damper state. Returns the same `userdata`.&#x20;
