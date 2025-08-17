---
description: >-
  The Vector API provides objects for performing mathematical operations in 2D,
  3D, and 4D space. These are essential for manipulating positions, directions,
  rotations, and colors. All vector operations
---

# Vector

### Vector2

A `Vector2` represents a point or direction in 2D space, containing `x` and `y` components.

#### Constructors

**`Vector2.new()`**

Creates a new `Vector2` with its components initialized to zero.

* **Returns:** (`Vector2`) A new vector at `(0, 0)`.

```lua
local MyVector = Vector2.new() -- MyVector is now (0, 0)
```

**`Vector2.new(x, y)`**

Creates a new `Vector2` with the specified components.

* **x:** (`number`) The value for the x-component.
* **y:** (`number`) The value for the y-component.
* **Returns:** (`Vector2`) A new vector with the given values.

```lua
local StartPosition = Vector2.new(100, 250)
```

#### Properties

**`x`**

* (`number`) The x-component of the vector. Can be read from or assigned to.

**`y`**

* (`number`) The y-component of the vector.

```lua
local MyVector = Vector2.new(10, 20)
print(MyVector.x) -- Outputs: 10

MyVector.y = 50
-- MyVector is now (10, 50)
```

#### Methods

**`vec:Length()`**

Calculates the magnitude (length) of the vector.

* **Returns:** (`number`) The length of the vector.

```lua
local MyVector = Vector2.new(3, 4)
local Length = MyVector:Length() -- Result is 5
```

**`vec:LengthSquared()`**

Calculates the squared length of the vector. This is faster than `Length()` as it avoids a square root operation and is useful for comparing distances. (I.e. when you don't require actual length but only knowledge what's closer or farther.)

* **Returns:** (`number`) The squared length of the vector.

```lua
local MyVector = Vector2.new(3, 4)
local LengthSquared = MyVector:LengthSquared() -- Result is 25
```

**`vec:FastLength()`**

Calculates an approximate length of the vector. This is less precise but computationally cheaper than `Length()`.

* **Returns:** (`number`) An approximation of the vector's length.

**`vec:Normalize()`**

Returns a new vector with the same direction but with a length of 1.

* **Returns:** (`Vector2`) The new, normalized vector.

```lua
local DirectionVector = Vector2.new(0, 5)
local NormalizedVector = DirectionVector:Normalize() -- NormalizedVector is (0, 1)
-- The original vector 'DirectionVector' remains unchanged.
```

#### Operators

`Vector2` objects support standard arithmetic operators.

```lua
local VectorOne = Vector2.new(10, 20)
local VectorTwo = Vector2.new(5, 5)

-- Vector-Vector operations
local ResultAdd = VectorOne + VectorTwo         -- (15, 25)
local ResultSubtract = VectorOne - VectorTwo    -- (5, 15)
local ResultMultiply = VectorOne * VectorTwo    -- (50, 100) (Component-wise multiplication)
local ResultDivide = VectorOne / VectorTwo      -- (2, 4)   (Component-wise division)

-- Vector-Scalar operations
local ResultScalarMultiply = VectorOne * 2      -- (20, 40)
local ResultScalarDivide = VectorOne / 10     -- (1, 2)
```

***

### Vector3

A `Vector3` represents a point or direction in 3D space, containing `x`, `y`, and `z` components.

#### Constructors

**`Vector3.new()`**

Creates a new `Vector3` with its components initialized to zero.

* **Returns:** (`Vector3`) A new vector at `(0, 0, 0)`.

**`Vector3.new(x, y, z)`**

Creates a new `Vector3` with the specified components.

* **x:** (`number`) The value for the x-component.
* **y:** (`number`) The value for the y-component.
* **z:** (`number`) The value for the z-component.
* **Returns:** (`Vector3`) A new vector with the given values.

```lua
local Position = Vector3.new(10, 50, -20)
```

#### Properties

**`x`, `y`, `z`**

* (`number`) The x, y, and z components of the vector. Can be read from or assigned to.

#### Methods

**`vec:Length()`**

Calculates the magnitude (length) of the vector.

* **Returns:** (`number`) The length of the vector.

**`vec:LengthSquared()`**

Calculates the squared length of the vector. Faster than `Length()`.

* **Returns:** (`number`) The squared length of the vector.

**`vec:FastLength()`**

Calculates an approximate length of the vector.

* **Returns:** (`number`) An approximation of the vector's length.

**`vec:Normalize()`**

Returns a new vector with the same direction but with a length of 1.

* **Returns:** (`Vector3`) The new, normalized vector.

**`vec:Dot(otherVec)`**

Calculates the dot product between this vector and another.

* **otherVec:** (`Vector3`) The other vector for the calculation.
* **Returns:** (`number`) The dot product.

```lua
local VectorOne = Vector3.new(1, 0, 0)
local VectorTwo = Vector3.new(0, 1, 0)
local DotProduct = VectorOne:Dot(VectorTwo) -- Result is 0 (vectors are perpendicular)
```

**`vec:Cross(otherVec)`**

Calculates the cross product between this vector and another, returning a new vector that is perpendicular to both.

* **otherVec:** (`Vector3`) The other vector for the calculation.
* **Returns:** (`Vector3`) The resulting perpendicular vector.

```lua
local XAxis = Vector3.new(1, 0, 0)
local YAxis = Vector3.new(0, 1, 0)
local CrossProduct = XAxis:Cross(YAxis) -- Result is (0, 0, 1), the Z-axis
```

**`vec:To2D()`**

Creates a `Vector2` by discarding the `z` component.

* **Returns:** (`Vector2`) A new `Vector2` with the `x` and `y` values of the `Vector3`.

```lua
local Vector3D = Vector3.new(10, 20, 30)
local Vector2D = Vector3D:To2D() -- Vector2D is (10, 20)
```

#### Operators

`Vector3` supports the same arithmetic operators as `Vector2` for both vector-vector and vector-scalar operations.

***

### Vector4

A `Vector4` represents a point in 4D space, containing `x`, `y`, `z`, and `w` components. Basically, a representation of a quaternion in our case.

#### Constructors

**`Vector4.new()`**

Creates a new `Vector4` with its components initialized to zero.

* **Returns:** (`Vector4`) A new vector at `(0, 0, 0, 0)`.

**`Vector4.new(x, y, z, w)`**

Creates a new `Vector4` with the specified components.

* **x, y, z, w:** (`number`) The values for the components.
* **Returns:** (`Vector4`) A new vector with the given values.

```lua
-- As a color with full alpha
local RedColor = Vector4.new(1, 0, 0, 1)
```

#### Properties

**`x`, `y`, `z`, `w`**

* (`number`) The x, y, z, and w components of the vector.

#### Methods

**`vec:ToEulerAngles()`**

Converts the `Vector4` (when used as a quaternion) into a `Vector3` representing Euler angles for rotation.

* **Returns:** (`Vector3`) A `Vector3` where x, y, and z correspond to pitch, yaw, and roll.

#### Operators

`Vector4` supports the same arithmetic operators as `Vector2` and `Vector3`.
