# Overview

This documentation describes Lua API for the https://pellix.xyz/

If you're not familiar with the Lua language please consider reading something like

{% embed url="https://learnxinyminutes.com/docs/lua/" %}

Please note that the previous link is suitable for people who already have any experience in the programming.&#x20;

For the official Lua API reference you can visit

{% embed url="https://www.lua.org/manual/5.1/" %}



Also in restricted mode (without `Allow Unsafe`) only `base`, `table`, `string`, `math` ,`bit`  and `string.buffer` (via `require`) libraries are available.

With `Allow Unsafe` , `io`, `debug` and `os` are available.

