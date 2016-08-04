This function gets the screen position of a point in the world. This is useful for attaching 2D gui elements to parts of the world (e.g. players) or detecting if a point is on the screen (though it does not check if it is actually visible, you should use [processLineOfSight](/docs/processlineofsight.md "wikilink") for that).

Syntax
------

``` lua
float float getScreenFromWorldPosition ( float x, float y, float z, [ float edgeTolerance=0, bool relative=true ] )
```

### Required Arguments

-   **x:** A float value indicating the x position in the world.
-   **y:** A float value indicating the y position in the world.
-   **z:** A float value indicating the z position in the world.

### Optional Arguments

### Returns

Returns two *x*, *y* [floats](/docs/float.md "wikilink") indicating the screen position and [float](/docs/float.md "wikilink") distance between screen and given position if successful, *false* otherwise.

### Example

<section class="client" name="Client-side Script" show="true">
This example add a '3d' text at coordinates 0, 0, 0 (center of map).

``` lua
addEventHandler ( "onClientRender", root,
function ( )
    if ( getDistanceBetweenPoints3D ( 0, 0, 3, getElementPosition ( localPlayer ) ) ) < 50 then
        local coords = { getScreenFromWorldPosition ( 0, 0, 3 ) }
        if coords[1] and coords[2] then
            dxDrawText ( "Hello !", coords[1], coords[2], coords[1], coords[2], tocolor(255,255,255), 1, "default-bold" )
        end
    end
end )
```

</section>
See Also
--------
