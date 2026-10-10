---
icon: crosshairs
---

# aimbot

{% code overflow="wrap" %}
```luau
aimbot.get_locked_target(): number | nil
```
{% endcode %}

Get current target player controller index locked by the aimbot, `nil` if there is no target.



{% code overflow="wrap" %}
```luau
aimbot.get_current_target(): number : nil
```
{% endcode %}

Get current target player controller index locked by the aimbot, `nil` if there is not target.



**aimbot\_settings**:

{% code overflow="wrap" %}
```luau
hitchance: number
smooth_type: number
min_aim_step: number
max_aim_step: number
fov: number
dead_zone: number
reaction_time: number
multipoints: number
smooth_x: number
smooth_y: number
recoil_mode: number
recoil_x: number
recoil_y: number
recoil_smooth_type: number
hitboxes: number
hitbox_priority: number
```
{% endcode %}



{% code overflow="wrap" %}
```luau
aimbot.get_settings(): aimbot_settings
```
{% endcode %}

Get current settings used by the aimbot.



