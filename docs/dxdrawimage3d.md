This function draws a textured 3D line between two points in the 3D world that appers to be a 3D image - rendered for one frame This should be used in conjunction with [onClientPreRender](/docs/onclientprerender.md "wikilink") in order to display continuously.

The 3D line with a large width value and a texture effectively becomes a 3D image, hence the possibility to construct basic shapes such as boxes with several large width lines and the appropriate values for 'faceToward'.

3D lines are drawn at a particular place in the [game processing order](/docs/game_processing_order.md "wikilink"), so use [onClientPreRender](/docs/onclientprerender.md "wikilink") for drawing if you are attaching them to world elements.
\* **NOTE:** This is made to be used clientside!.

Syntax
------

``` lua
```

### Required Arguments

-   **X/Y/Z:** The start position of the 3D image, representing a coordinate in the GTA world.
-   **width:** The width of the image in GTA world units. (This is 1/75th of the width used in dxDrawLine3D)
-   **height:** The height of the image in GTA world units. (This is 1/75th of the width used in dxDrawLine3D)
-   **material:** A material to draw the image with.

Optional Arguments
------------------

-   **color:** An integer of the hex color, produced using [tocolor](/docs/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **rotation:** Rotation (end point of the image) offset
-   **faceTowardX/Y/Z:** The direction the front of the image should face towards. If this is not set, the front of the image always faces toward the camera.

### Returns

Returns a *true* if the operation was successful, *false* otherwise.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
local white = tocolor(255,255,255,255)
function dxDrawImage3D(x,y,z,w,h,m,c,r,...)
        local lx, ly, lz = x+w, y+h, (z+tonumber(r or 0)) or z
    return dxDrawMaterialLine3D(x,y,z, lx, ly, lz, m, h, c or white, ...)
end
```

</section>
Example
-------

This draws a trollface in the middle of the GTA world for no reason

``` lua
local face = dxCreateTexture("trollface.png")
addEventHandler("onClientRender", root,
    function()
        dxDrawImage3D(0,0, 20, 20, 20, face, tocolor(255,255,255,255))
    end
)
```

Author: qaisjp

See Also
--------
