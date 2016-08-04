This function gets an [element](/element.md "wikilink")'s transform [matrix](/matrix.md "wikilink"). This contains 16 float values that multiplied to a point will give you the point transformed. It is most useful for matrix calculations such as calculating offsets. For further information, please refer to a tutorial of matrices in computer graphics programming. 6984 not setup correctly for some calculations\] unless the **legacy** argument is set to ***false***.}}

Syntax
------

``` lua
table getElementMatrix ( element theElement [, bool legacy = true ] )
```

### Required Arguments

-   **theElement:** The [element](/element.md "wikilink") which you wish to retrieve the [matrix](/matrix.md "wikilink") for.

### Optional Arguments

-   **legacy:** Set to *false* to return correctly setup [matrix](/matrix.md "wikilink") (i.e. Last column in the first 3 rows set to zero).

### Returns

Returns a multi-dimensional array (which can be transformed into a proper [matrix](/matrix.md "wikilink") class using *Matrix.create* method) containing a 4x4 matrix. Returns *false* if the element is not streamed in, and not a [vehicle](/vehicle.md "wikilink"), [ped](/ped.md "wikilink") or [object](/object.md "wikilink").

Example
-------

This example creates a utility function that turns an offset into a position that is relative to the specified element.

``` lua
function getPositionFromElementOffset(element,offX,offY,offZ)
    local m = getElementMatrix ( element )  -- Get the matrix
    local x = offX * m[1][1] + offY * m[2][1] + offZ * m[3][1] + m[4][1]  -- Apply transform
    local y = offX * m[1][2] + offY * m[2][2] + offZ * m[3][2] + m[4][2]
    local z = offX * m[1][3] + offY * m[2][3] + offZ * m[3][3] + m[4][3]
    return x, y, z                               -- Return the transformed point
end

-- Get the position of a point 3 units to the right of the element:
x,y,z = getPositionFromElementOffset(element,3,0,0)

-- Get the position of a point 2 units in front of the element:
x,y,z = getPositionFromElementOffset(element,0,2,0)

-- Get the position of a point 1 unit above the element:
x,y,z = getPositionFromElementOffset(element,0,0,1)
```

This example creates some more matrix utility functions

``` lua
function getMatrixLeft(m)
    return m[1][1], m[1][2], m[1][3]
end
function getMatrixForward(m)
    return m[2][1], m[2][2], m[2][3]
end
function getMatrixUp(m)
    return m[3][1], m[3][2], m[3][3]
end
function getMatrixPosition(m)
    return m[4][1], m[4][2], m[4][3]
end

local mat = getElementMatrix(element)  -- Get the matrix
x,y,z = getMatrixLeft(mat)     -- Get the matrix left direction
x,y,z = getMatrixForward(mat)  -- Get the matrix forward direction
x,y,z = getMatrixUp(mat)       -- Get the matrix up direction
```

This example function allows you to get the element matrix of an element that is not streamed in.

``` lua
function getElementMatrix(element)
    local rx, ry, rz = getElementRotation(element, "ZXY")
    rx, ry, rz = math.rad(rx), math.rad(ry), math.rad(rz)
    local matrix = {}
    matrix[1] = {}
    matrix[1][1] = math.cos(rz)*math.cos(ry) - math.sin(rz)*math.sin(rx)*math.sin(ry)
    matrix[1][2] = math.cos(ry)*math.sin(rz) + math.cos(rz)*math.sin(rx)*math.sin(ry)
    matrix[1][3] = -math.cos(rx)*math.sin(ry)
    matrix[1][4] = 1
    
    matrix[2] = {}
    matrix[2][1] = -math.cos(rx)*math.sin(rz)
    matrix[2][2] = math.cos(rz)*math.cos(rx)
    matrix[2][3] = math.sin(rx)
    matrix[2][4] = 1
    
    matrix[3] = {}
    matrix[3][1] = math.cos(rz)*math.sin(ry) + math.cos(ry)*math.sin(rz)*math.sin(rx)
    matrix[3][2] = math.sin(rz)*math.sin(ry) - math.cos(rz)*math.cos(ry)*math.sin(rx)
    matrix[3][3] = math.cos(rx)*math.cos(ry)
    matrix[3][4] = 1
    
    matrix[4] = {}
    matrix[4][1], matrix[4][2], matrix[4][3] = getElementPosition(element)
    matrix[4][4] = 1
    
    return matrix
end
```

Changelog
---------

See Also
--------
