Sets the world position of a corner point of a water area.

Syntax
------

``` lua
bool setWaterVertexPosition ( water theWater, int vertexIndex, int x, int y, float z )
```

### Required Arguments

-   **theWater:** the water element of which to change a vertex.
-   **vertexIndex:** the index of the vertex to move. Values range from 1 to 4 for water quads, and 1 to 3 for triangles.
-   **x:** the X coordinate to set for the vertex.
-   **y:** the Y coordinate to set for the vertex.
-   **z:** the Z coordinate to set for the vertex.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

``` lua
--TODO
```

See Also
--------
