Gets the world position of a vertex (i.e. corner) of a [water](/water.md "wikilink") area. Each water area is either a triangle or quad (rectangle) so each has 3 or 4 corners.

Syntax
------

``` lua
int int float getWaterVertexPosition ( water theWater, int vertexIndex )
```

### Required Arguments

-   **theWater:** the water element to get the vertex of
-   **vertexIndex:** the index of the vertex whose position to get. Values range from 1 to 4 for a water quad, or 1 to 3 for a triangle.

### Returns

Returns the x, y and z coordinates of the specified vertex if successful, *false* otherwise.

Example
-------

``` lua
--TODO
```

See Also
--------
