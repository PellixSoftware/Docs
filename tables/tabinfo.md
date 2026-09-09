---
description: Allows to access tab info information.
icon: list-ul
---

# tabinfo

player\_info:

{% code overflow="wrap" %}
```luau
steamid: uint64_t
steam_country_code: string

faceit_level: number | -1
faceit_elo: number | 0
faceit_verified: boolean
faceit_nickname: string
faceit_country_code: string
has_faceit_info: boolean

leetify_aim_rating: number
leetify_preaim: number
leetify_reaction_time: number
leetify_kd: number
has_leetify_info: boolean

csrep_preaim: number
csrep_ttd: number
csrep_winrate: number
csrep_kd: number
has_csrep_info: boolean
```
{% endcode %}



{% code overflow="wrap" %}
```luau
tabinfo.get_player_info(steamid: uint64_t): player_info
```
{% endcode %}

Retrieves fetched player data by steamid from tabinfo cache.

