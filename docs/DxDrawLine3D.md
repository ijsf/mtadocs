This function draws a 3D line between two points in the 3D world - rendered for **one** frame. This should be used in conjunction with [onClientRender](/docs/onClientRender.md "wikilink") in order to display continuously.

Syntax
------

``` lua
bool dxDrawLine3D ( float startX, float startY, float startZ, float endX, float endY, float endZ[, int color = white, int width = 1, bool postGUI = false ] )
```

### Required Arguments

-   **startX:** The start X position of the 3D line, representing a coordinate in the GTA world.
-   **startY:** The start Y position of the 3D line, representing a coordinate in the GTA world.
-   **startZ:** The start Z position of the 3D line, representing a coordinate in the GTA world.
-   **endX:** The end X position of the 3D line, representing a coordinate in the GTA world.
-   **endY:** The end Y position of the 3D line, representing a coordinate in the GTA world.
-   **endZ:** The end Z position of the 3D line, representing a coordinate in the GTA world.

Optional Arguments
------------------

-   **color:** An integer of the hex color, produced using [tocolor](/docs/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **width:** The width/thickness of the line
-   **postGUI:** A bool representing whether the line should be drawn on top of or behind any ingame GUI (rendered by CEGUI).

### Returns

Returns a *true* if the operation was successful, *false* otherwise.

Example
-------

This is a small example of creating 3D Line / “Rope” between vehicle and player.

``` lua
function makeLineAppear()
    testVehicle = createVehicle ( 411, 0, 0, 5 ) -- Create our test vehicle.
    addEventHandler("onClientRender", root, createLine)        -- onClientRender keeps the 3D Line visible.
end
function createLine ( )
    x1, y1, z1 = getElementPosition ( testVehicle )                       -- Get test vehicles position.
    x2, y2, z2 = getElementPosition ( localPlayer )                  -- Get local players position.
    dxDrawLine3D ( x1, y1, z1, x2, y2, z2, tocolor ( 0, 255, 0, 230 ), 2) -- Create 3D Line between test vehicle and local player.
end
addCommandHandler("test", makeLineAppear)
```

See Also
--------
