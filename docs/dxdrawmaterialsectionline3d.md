This function draws a textured 3D line between two points in the 3D world - rendered for one frame. This should be used in conjunction with [onClientPreRender](/docs/onclientprerender.md "wikilink") in order to display continuously.

The 3D line with a large width value effectively becomes a rectangle, so it it possible to construct basic shapes such as boxes with several large width lines and the appropriate values for 'faceToward'.

Syntax
------

``` lua
bool dxDrawMaterialSectionLine3D ( float startX, float startY, float startZ, float endX, float endY, float endZ,
                                   float u, float v, float usize, float vsize, element material, int width,
                                 [ int color = white, float faceTowardX, float faceTowardY, float faceTowardZ ] )
```

### Required Arguments

-   **startX/Y/Z:** The start position of the 3D line, representing a coordinate in the GTA world.
-   **endX/Y/Z:** The end position of the 3D line, representing a coordinate in the GTA world.
-   **u:** the absolute X coordinate of the top left corner of the section
-   **v:** the absolute Y coordinate of the top left corner of the section
-   **usize:** the absolute width of the section
-   **vsize:** the absolute height of the section
-   **material:** A [material](/docs/material.md "wikilink") to draw the line with.
-   **width:** The width/thickness of the line in GTA world units. (This is 1/75th of the width used in dxDrawLine3D)

Optional Arguments
------------------

-   **color:** An integer of the hex color, produced using [tocolor](/docs/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **faceTowardX/Y/Z:** The direction the front of the line should face towards. If this is not set, the front of the line always faces toward the camera.

### Returns

Returns a *true* if the operation was successful, *false* otherwise.

Example
-------

This example draws corona like effects near the player

``` lua
coronaTexture = dxCreateTexture("corona.png")
red = tocolor(255,0,0)
green = tocolor(0,255,0)
blue = tocolor(0,0,255)

addEventHandler("onClientPreRender",root,
    function()
        local x,y,z = getElementPosition(localPlayer)

        dxSetBlendMode("add")   -- Add blend mode looks best for corona effects
        drawCorona( x+2, y+2, z+1, 1, red )
        drawCorona( x+1, y+3, z+2, 1, green )
        drawCorona( x-1, y+2, z+3, 1, blue )
        dxSetBlendMode("blend") -- Restore default
    end
)

-- Draw the corona texture
function drawCorona( x, y, z, size, color )
    dxDrawMaterialSectionLine3D ( x, y, z+size,
                                  x, y, z-size,
                                  0,0,1,1, coronaTexture, size, color)
end
```

Requirements
------------

See Also
--------
