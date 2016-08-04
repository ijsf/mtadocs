This function draws a textured 3D line between two points in the 3D world that appers to be a rectangle - rendered for one frame This should be used in conjunction with [onClientPreRender](/docs/onclientprerender.md "wikilink") in order to display continuously.

The 3D line with a large width value effectively becomes a rectangle, hence the possibility to construct basic shapes such as boxes with several large width lines and the appropriate values for 'faceToward'.

3D lines are drawn at a particular place in the [game processing order](/docs/game_processing_order.md "wikilink"), so use [onClientPreRender](/docs/onclientprerender.md "wikilink") for drawing if you are attaching them to world elements.
\* **NOTE:** This is made to be used clientside!.

Syntax
------

``` lua
```

### Required Arguments

-   **X/Y/Z:** The start position of the 3D rectangle, representing a coordinate in the GTA world.
-   **width:** The width of the rect in GTA world units. (This is 1/75th of the width used in dxDrawLine3D)
-   **height:** The height of the rect in GTA world units. (This is 1/75th of the width used in dxDrawLine3D)

Optional Arguments
------------------

-   **color:** An integer of the hex color, produced using [tocolor](/docs/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **rotation:** Rotation (end point of the rect) offset
-   **faceTowardX/Y/Z:** The direction the front of the rect should face towards. If this is not set, the front of the rect always faces toward the camera.

### Returns

Returns a *true* if the operation was successful, *false* otherwise.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
local dot = dxCreateTexture(1,1)
local white = tocolor(255,255,255,255)
function dxDrawRectangle3D(x,y,z,w,h,c,r,...)
        local lx, ly, lz = x+w, y+h, (z+tonumber(r or 0)) or z
    return dxDrawMaterialLine3D(x,y,z, lx, ly, lz, dot, h, c or white, ...)
end
```

</section>
Example
-------

This draws a white rectangle in the middle of the GTA world for no reason

``` lua
addEventHandler("onClientRender", root,
    function()
        dxDrawRectangle3D(0,0, 20, 20, 20, tocolor(255,255,255,255))
    end
)
```

Author: qaisjp

See Also
--------
