<lowercasetitle/>

This function draws a number of 2D lines in order to achieve a circle shape on the screen - rendered for **one** frame. This should be used in conjunction with [onClientRender](/docs/onclientrender.md "wikilink") in order to display continuously.

Syntax
------

``` lua
 )
```

### Required Arguments

[thumb|An example of how dxDrawCircle function works in practice.](/docs/image-dxdrawcircle_example.png.md "wikilink")

-   **posX**: An integer representing the **absolute** X position of the circle center, represented by pixels on the screen.
-   **posY**: An integer representing the **absolute** Y position of the circle center, represented by pixels on the screen.

### Optional Arguments

-   **radius**: An integer representing the radius scale of the circle that is being drawn.
-   **width**: An integer representing the width of the line that is being drawn.
-   **angleAmount**: An integer representing the tightness of the circle. Lower amount makes it smoother, higher amount makes it more of a clock looking circle.
-   **startAngle**: An integer representing the angle of the first point of the circle.
-   **stopAngle**: An integer representing the angle of the last point of the circle.
-   **color**: An integer of the hex color, produced using [tocolor](/docs/tocolor.md "wikilink") or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue).
-   **postGUI**: A bool representing whether the line should be drawn on top of or behind any ingame GUI (rendered by CEGUI).

### Returns

Returns *true* if the creation of the 2D circle was successful, *false* otherwise.

Code
----

<section name="Client" class="client" show="true">
``` lua
function dxDrawCircle( posX, posY, radius, width, angleAmount, startAngle, stopAngle, color, postGUI )
    if ( type( posX ) ~= "number" ) or ( type( posY ) ~= "number" ) then
        return false
    end
    
    local function clamp( val, lower, upper )
        if ( lower > upper ) then lower, upper = upper, lower end
        return math.max( lower, math.min( upper, val ) )
    end
    
    radius = type( radius ) == "number" and radius or 50
    width = type( width ) == "number" and width or 5
    angleAmount = type( angleAmount ) == "number" and angleAmount or 1
    startAngle = clamp( type( startAngle ) == "number" and startAngle or 0, 0, 360 )
    stopAngle = clamp( type( stopAngle ) == "number" and stopAngle or 360, 0, 360 )
    color = color or tocolor( 255, 255, 255, 200 )
    postGUI = type( postGUI ) == "boolean" and postGUI or false
    
    if ( stopAngle < startAngle ) then
        local tempAngle = stopAngle
        stopAngle = startAngle
        startAngle = tempAngle
    end
    
    for i = startAngle, stopAngle, angleAmount do
        local startX = math.cos( math.rad( i ) ) * ( radius - width )
        local startY = math.sin( math.rad( i ) ) * ( radius - width )
        local endX = math.cos( math.rad( i ) ) * ( radius + width )
        local endY = math.sin( math.rad( i ) ) * ( radius + width )
    
        dxDrawLine( startX + posX, startY + posY, endX + posX, endY + posY, color, width, postGUI )
    end
    
    return true
end
```

</section>
**Author:** Socialz
==Examples==

<section name="Client" class="client" show="true">
This example draws a progressing circle shape in the middle of the screen.

``` lua
local screenWidth, screenHeight = guiGetScreenSize( )
local stopAngle = 0

addEventHandler( "onClientRender", root,
    function( )
        if ( stopAngle < 360 ) then
            stopAngle = stopAngle + 5
        else
            stopAngle = 0
        end
        
        dxDrawCircle( screenWidth / 2, screenHeight / 2, nil, nil, nil, nil, stopAngle )
    end
)
```

</section>
<section name="Client" class="client" show="true">
This example draws the shape of a circle arc with an angle of 90°.

``` lua
addEventHandler( "onClientRender", root, 
    function( )
        -- We're starting to draw the circle at 0° which means that the first point of the arc is ( 200+50 | 200 )
        -- Therefore the last point is ( 200 | 200+50 ). > Our arc is the "lower right" quarter of the circle.
        dxDrawCircle( 200, 200, 50, 5, 1, 0, 90 )
    end
)
```

Example by: Michael89/Trevit

</section>
See Also
--------
