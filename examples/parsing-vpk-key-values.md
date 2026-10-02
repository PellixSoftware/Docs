# Parsing VPK key values

{% code overflow="wrap" %}
```lua
local file = vpk.read_file("panorama/images/econ/status_icons/10yearcoin_png.vtex_c")

local function resource_callback(signature, offset, size, index, data)
    if signature == 0x32444552 then
       local kv3 = vpk.parse_binary_kv3(data)
       print("kv3 version:", kv3.version)
       
       local value = kv3.root:get("m_ArgumentDependencies"):get(1):get("m_ParameterName").value
       
       -- ___OverrideInputData___
       print(value)
    end
    
    return true
end

vpk.parse_resource(file, resource_callback)
```
{% endcode %}

