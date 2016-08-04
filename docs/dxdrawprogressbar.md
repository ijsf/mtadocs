<lowercasetitle/>

This function simulates a progress bar drawed using DirectDraw. (Note this will only work client-side and you need to call it on each frame)

Syntax
------

``` lua
dxDrawProgressBar(float startX, float startY, float width, float height, float progress, int color, int backColor)
```

### Required arguments

-   **startX**: An float representing the absolute origin X position of the rectangle, represented by pixels on the screen.
-   **startY**: An float representing the absolute origin Y position of the rectangle, represented by pixels on the screen.
-   **width**: An float representing the width of the rectangle, drawn in a *right* direction from the origin.
-   **height**: An float representing the height of the rectangle, drawn in a *downwards* direction from the origin.
-   **progress**: a float ranging from 0 to 100
-   **color**: the hex color of the progress bar, produced using tocolor or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue)
-   **backColor**: the hex color of the background, produced using tocolor or 0xAARRGGBB (AA = alpha, RR = red, GG = green, BB = blue)

### Return

None

Code
----

``` lua
local unlerp = function(from,to,lerp) return (lerp-from)/(to-from) end
 
function dxDrawProgressBar( startX, startY, width, height, progress, color, backColor )
        local progress = math.max( 0, (math.min( 100, progress) ) )
        local wBar = width*.18
        for i = 0, 4 do
                --back
                local startPos = (wBar*i + (width*.025)*i) + startX
                dxDrawRectangle( startPos, startY, wBar, height, backColor )
                --progress
                local eInterval = (i*20)
                local localProgress = math.min( 1, unlerp( eInterval, eInterval + 20, progress ) )
                        if localProgress > 0 then
                                dxDrawRectangle( startPos, startY, wBar*localProgress, height, color )
                        end
        end
end
```

Example
-------

<section name="Example" class="client" show="true">
This example draws a progress bar in the top-left corner of the screen, with a random progress that changes every frame.

``` lua
function draw()
  dxDrawProgressBar( 10, 10, 200, 200, math.random(0,100), tocolor( 250, 50, 50, 255), tocolor( 255, 255, 255, 255) )
end
addEventHandler("onClientRender", root, draw)  -- Keep everything visible with onClientRender.
```

</section>
See Also
--------
