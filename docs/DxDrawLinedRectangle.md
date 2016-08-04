[:Category:Useful\_Functions](/:Category:Useful_Functions.md "wikilink")

This is a function that will create a rectangle outline with dx lines.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **x:** An integer representing the absolute start X position of the line, represented by pixels on the screen.
-   **y:** An integer representing the absolute start Y position of the line, represented by pixels on the screen.
-   **width:** An float representing the width of the area, drawn in a right direction from the origin.
-   **height:** An float representing the height of the rectangle, drawn in a downwards direction from the origin.
-   **color:** the hex color of the rectangle, produced using tocolor or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).

Optional Arguments
------------------

-   **width:** An integer representing how thick the lines will be.
-   **postGUI:** A bool representing whether the line should be drawn on top of or behind any ingame GUI.

### Returns

Returns a *true* if the operation was successful, *false* otherwise.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function dxDrawLinedRectangle( x, y, width, height, color, _width, postGUI )
    local _width = _width or 1
    dxDrawLine ( x, y, x+width, y, color, _width, postGUI ) -- Top
    dxDrawLine ( x, y, x, y+height, color, _width, postGUI ) -- Left
    dxDrawLine ( x, y+height, x+width, y+height, color, _width, postGUI ) -- Bottom
    return dxDrawLine ( x+width, y, x+width, y+height, color, _width, postGUI ) -- Right
end
```

</section>
Example
-------

This draws a green rectangle:

``` lua
local sx, sy = guiGetScreenSize ( )
addEventHandler("onClientRender", root,
    function()
        dxDrawLinedRectangle( 5, 5, sx/2, sy/2, tocolor ( 0, 255, 0, 255 ), 3, true )
    end
)
```

Author: xXMADEXx

See Also
--------
