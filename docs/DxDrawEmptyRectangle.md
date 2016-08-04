This function creates an empty dx rectangle. (Note this will only work client-side and you need to call it on each frame)

Syntax
------

``` lua
 )
```

### Required Arguments

-   **startX:** An float representing the **absolute** origin X position of the rectangle, represented by pixels on the screen.
-   **startY:** An float representing the **absolute** origin Y position of the rectangle, represented by pixels on the screen.
-   **endX:** An float representing the width of the rectangle, drawn in a *right* direction from the origin.
-   **endY:** An float representing the height of the rectangle, drawn in a *downwards* direction from the origin.
-   **color:** the hex color of the rectangle, produced using [tocolor](/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).

### Optional Arguments

-   **width:** The width/thickness of the line
-   **postGUI:** A bool representing whether the rectangle should be drawn on top of or behind any ingame GUI.

Code
----

    [lua]
    function dxDrawEmptyRectangle(startX, startY, endX, endY, color, width, postGUI)
        dxDrawLine ( startX, startY, startX+endX, startY, color, width, postGUI )
        dxDrawLine ( startX, startY, startX, startY+endY, color, width, postGUI )
        dxDrawLine ( startX, startY+endY, startX+endX, startY+endY,  color, width, postGUI )
        dxDrawLine ( startX+endX, startY, startX+endX, startY+endY, color, width, postGUI )
    end

Example
-------

``` lua
addEventHandler( "onClientRender", root,
    function()
        dxDrawEmptyRectangle( 350, 350, 100, 100, tocolor(255,0,255), 1, false )
    end
)
```

See Also
--------
