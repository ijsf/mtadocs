This function draws a textured 3D line between two points in the 3D world - rendered for one frame. This should be used in conjunction with [onClientPreRender](/docs/onclientprerender.md "wikilink") in order to display continuously.

The 3D line with a large width value effectively becomes a rectangle, so it it possible to construct basic shapes such as boxes with several large width lines and the appropriate values for 'faceToward'.

3D lines are drawn at a particular place in the [game processing order](/docs/game_processing_order.md "wikilink"), so use [onClientPreRender](/onClientPreRender.md "wikilink") for drawing if you are attaching them to world elements.

Syntax
------

``` lua
bool dxDrawMaterialLine3D ( float startX, float startY, float startZ, float endX, float endY, float endZ, element material, float width,
                          [ int color = white, float faceTowardX, float faceTowardY, float faceTowardZ ] )
```

### Required Arguments

-   **startX/Y/Z:** The start position of the 3D line, representing a coordinate in the GTA world.
-   **endX/Y/Z:** The end position of the 3D line, representing a coordinate in the GTA world.
-   **material:** A [material](/docs/material.md "wikilink") to draw the line with.
-   **width:** The width/thickness of the line in GTA world units. (This is 1/75th of the width used in dxDrawLine3D)

Optional Arguments
------------------

-   **color:** An [integer](/docs/int.md "wikilink") of the hex color, produced using [tocolor](/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **faceTowardX/Y/Z:** The position the front of the line should face towards. If this is not set, the camera position is used, so the front of the line faces toward the camera.

### Returns

Returns a *true* if the operation was successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
Draws an Image ( “test.png” Download : [test.png](http://i.epvpimg.com/dwsTe.png) ) from the Position 0,0,3 to 0,0,15

    local img = dxCreateTexture("test.png")
    addEventHandler("onClientRender", root,
        function()  -- x,y,z, targetx,targety,targetz,texture,width,color
            dxDrawMaterialLine3D (0,0,3,0,0,15,img, 7, tocolor(255,255,255,255))
        end)

</section>
Requirements
------------

See Also
--------
