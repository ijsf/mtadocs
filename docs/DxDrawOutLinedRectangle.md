<lowercasetitle/>

This function allows you to create the out lined rectangle.

Syntax
------

``` lua
bool dxDrawOutLinedRectangle( float x, float y, float width, float height[, int color = white, bool postGUI = false, bool subPixelPos= false ])
```

### Required Arguments

-   **x:** A float representing the **absolute** origin X position of the rectangle, represented by pixels on the screen.
-   **y:** A float representing the **absolute** origin Y position of the rectangle, represented by pixels on the screen.
-   **width:** A float representing the width of the rectangle, drawn in a *right* direction from the origin.
-   **height:** A float representing the height of the rectangle, drawn in a *downwards* direction from the origin.

### Optional Arguments

-   **color:** the hex color of the rectangle, produced using [tocolor](/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **postGUI:** A bool representing whether the line should be drawn on top of or behind any ingame GUI.

### Returns

Returns true if the operation was successful, false otherwise.

Function
--------

``` lua
function dxDrawOutLinedRectangle(x ,y, w, h, color, postGUI, subPixelPos)
    dxDrawRectangle(x, y, w, h, color, postGUI, subPixelPos)
    dxDrawLine(x - 1, y - 1, x - 1, y + h, tocolor ( 0, 0, 0, 255 ), 1, false)
    dxDrawLine(x + w, y - 1, x - 1, y - 1, tocolor ( 0, 0, 0, 255 ), 1, false)
    dxDrawLine(x - 1, y + h, x + w, y + h, tocolor ( 0, 0, 0, 255 ), 1, false)
    dxDrawLine(x + w, y + h, x + w, y - 1, tocolor ( 0, 0, 0, 255 ), 1, false)
end 
```

Example
-------

<section name="Example" class="client" show="true">
This example creates an out lined rectangle.

``` lua
function dxDrawOutLinedRectangle(x ,y, w, h, color, postGUI, subPixelPos)
    dxDrawRectangle(x, y, w, h, color, postGUI, subPixelPos)
    dxDrawLine(x - 1, y - 1, x - 1, y + h, tocolor ( 0, 0, 0, 255 ), 1, false)
    dxDrawLine(x + w, y - 1, x - 1, y - 1, tocolor ( 0, 0, 0, 255 ), 1, false)
    dxDrawLine(x - 1, y + h, x + w, y + h, tocolor ( 0, 0, 0, 255 ), 1, false)
    dxDrawLine(x + w, y + h, x + w, y - 1, tocolor ( 0, 0, 0, 255 ), 1, false)
end 

addEventHandler("onClientRender", getRootElement() ,
function()
    dxDrawOutLinedRectangle(900, 450, 250, 160, tocolor(255, 50, 50, 150), false)
end) 
```

</section>
Author: KariM

See Also
--------
