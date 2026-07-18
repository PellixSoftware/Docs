---
description: Allows to manipulate JSON.
icon: brackets-curly
---

# json

```luau
json.parse(data: string): table | nil
```

Parses JSON string from buffer.



```luau
json.stringify(data: table [, indent: 2 | 4]): string | nil
```

Converts lua table to UTF-8 JSON string. Indent specifies amount of spaces to pad with (only 2 or 4).



```luau
json.parse_fast(data: string): userdata | nil
```

Parses JSON string from buffer. This function returns a read-only table-like userdata.

This function is faster than `json.parse` because it doesn't convert JSON to lua table but returns an immutable object.

