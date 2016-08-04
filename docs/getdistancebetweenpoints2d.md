This function returns the distance between two 2 dimensional points using the pythagorean theorem.

Syntax
------

``` lua
float getDistanceBetweenPoints2D ( float x1, float y1, float x2, float y2 )
```

### Required Arguments

-   **x1**: The X position of the first point
-   **y1**: The Y position of the first point
-   **x2**: The X position of the second point
-   **y2**: The Y position of the second point

### Returns

Returns a float containing the 2D distance between the two points. Returns *false* if invalid parameters are passed.

Example
-------

<section name="Server and client" class="both" show="true">
This example gets the distance between two vehicles, stored in variables *vehicle1* and *vehicle2*.

``` lua
vehicle1x, vehicle1y, vehicle1z = getElementPosition ( vehicle1 )
vehicle2x, vehicle2y, vehicle2z = getElementPosition ( vehicle2 )
outputChatBox ( "The map distance between vehicle1 and vehicle2 is ", getDistanceBetweenPoints2D ( vehicle1x, vehicle1y, vehicle2x, vehicle2y ) )
```

</section>
See Also
--------
