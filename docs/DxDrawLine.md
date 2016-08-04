This function draws a 2D line across the screen - rendered for **one** frame. This should be used in conjunction with [onClientRender](/onClientRender.md "wikilink") in order to display continuously.

Syntax
------

``` lua
bool dxDrawLine ( int startX, int startY, int endX, int endY, int color, [float width=1, bool postGUI=false] )
```

### Required Arguments

-   **startX:** An integer representing the **absolute** start X position of the line, represented by pixels on the screen.
-   **startY:** An integer representing the **absolute** start Y position of the line, represented by pixels on the screen.
-   **endX:** An integer representing the **absolute** end X position of the line, represented by pixels on the screen.
-   **endY:** An integer representing the **absolute** end Y position of the line, represented by pixels on the screen.
-   **color:** An integer of the hex color, produced using [tocolor](/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).

Optional Arguments
------------------

-   **width:** The width/thickness of the line
-   **postGUI:** A bool representing whether the line should be drawn on top of or behind any ingame GUI (rendered by CEGUI).

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

This example draws an 'X' across the screen.

``` lua
local screenWidth, screenHeight = guiGetScreenSize() 
local lineColor = tocolor(255, 0, 0)
function drawLinesAcrossScreen()
    dxDrawLine(0, 0, screenWidth, screenHeight, lineColor)
    dxDrawLine(screenWidth, 0, 0, screenHeight, lineColor)
end
addEventHandler("onClientRender", root, drawLinesAcrossScreen)
```

This example draws a couple of circles

``` lua
function drawCircle( x,y, radius, color )
    local numPoints = math.floor( math.pow( radius, 0.4 ) * 5 )     -- Calculate number of points to make it look good
    local step = math.pi * 2 / numPoints
    local sx,sy
    for p=0,numPoints do
        local ex = math.cos ( p * step ) * radius
        local ey = math.sin ( p * step ) * radius
        if sx then
            dxDrawLine( x+sx, y+sy, x+ex, y+ey, color )
        end
        sx,sy = ex,ey
    end
end

addEventHandler( "onClientRender", root,
    function()
        drawCircle( 350, 350, 10, tocolor(255,0,255) );
        drawCircle( 350, 350, 50, tocolor(255,0,255) );
    end
)
```

See Also
--------
