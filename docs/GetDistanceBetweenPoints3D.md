This function returns the distance between two 3 dimensional points using the pythagorean theorem.

Syntax
------

``` lua
float getDistanceBetweenPoints3D ( float x1, float y1, float z1, float x2, float y2, float z2 )
```

### Required Arguments

-   **x1**: The X position of the first point
-   **y1**: The Y position of the first point
-   **z1**: The Z position of the first point
-   **x2**: The X position of the second point
-   **y2**: The Y position of the second point
-   **z2**: The Z position of the second point

### Returns

Returns a float containing the distance between the two points as a [float](/float.md "wikilink"). Returns *false* if an argument passed was invalid.

Example
-------

This example gets the distance between two vehicles and outputs it to the chat box.

``` lua
vehicle1x, vehicle1y, vehicle1z = getElementPosition ( vehicle1 )
vehicle2x, vehicle2y, vehicle2z = getElementPosition ( vehicle2 )
outputChatBox ( "The distance between vehicle1 and vehicle2 is "..tostring(getDistanceBetweenPoints3D ( vehicle1x, vehicle1y, vehicle1z, vehicle2x,
 vehicle2y, vehicle2z )) )
```

*getDistanceBetweenPoints3D* can also be used to measure the length of 3 dimensional vectors. This example calculates the speed of a vehicle by measuring the size of the it's velocity vector:

``` lua
speed = getDistanceBetweenPoints3D ( 0, 0, 0, getElementVelocity ( vehicle ) )
```

*Lua note: Using multiple return values as arguments for another function can only be done at the end of the argument list.*

See Also
--------
