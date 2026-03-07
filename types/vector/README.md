---
icon: triangle
---

# vector

```cpp
vector.new(x: number, y: number [, z: number, w: number ]): vector<dimensions>
```

Creates a new vector with up to 4 dimensions.



**Fields:**

```
x: number
y: number
z: number
w: number
```

Fields also can be accessed with index operator \[].



**Methods:**

```lua
length(): number -- vector
length_sqr(): number -- vector length squared
tostring(): string -- vector<?>(x, y, ...)
```



**Operators:**

```lua
__add(a: vector<x>, b: vector<x>): vector<x> -- c = a + b
__sub(a: vector<x>, b: vector<x>): vector<x> -- c = a - b
__mul(a: vector<x>, b: vector<x>): vector<x> -- c = a * b
__div(a: vector<x>, b: vector<x>): vector<x> -- c = a / b 
__unm(a: vector<x>): vector<x>               -- c = -a
```



**Example:**

```lua
local pos = vector.new(0, 0) -- vector<2>(0, 0)
pos.x = 30
pos.y = 50
-- vector<2>(30, 50)

pos = vector.new(0, 0, 0)
pos[1] = 10
pos[2] = 30
--- vector<3>(10, 30, 0)
```
