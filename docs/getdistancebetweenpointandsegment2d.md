<lowercasetitle></lowercasetitle>

Takes point coordinates and line (a segment) starting and ending coordinates. It returns the shortest distance between the point and the line.

Syntax
------

``` lua
float getDistanceBetweenPointAndSegment2D(float pointX, float pointY, float x1, float y1, float x2, float y2)
```

### Required Arguments

-   **pointX**: The X coordinate of the point.
-   **pointY**: The Y coordinate of the point.
-   **x1**: The X coordinate of the starting point of the line.
-   **y1**: The Y coordinate of the starting point of the line.
-   **x2**: The X coordinate of the ending point of the line.
-   **y2**: The Y coordinate of the ending point of the line.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getDistanceBetweenPointAndSegment2D(pointX, pointY, x1, y1, x2, y2)
    local A = pointX - x1
    local B = pointY - y1
    local C = x2 - x1
    local D = y2 - y1

    local point = A * C + B * D
    local lenSquare = C * C + D * D
    local parameter = point / lenSquare

    local shortestX
    local shortestY

    if parameter < 0 then
        shortestX = x1
            shortestY = y1
    elseif parameter > 1 then
        shortestX = x2
        shortestY = y2
    else
        shortestX = x1 + parameter * C
        shortestY = y1 + parameter * D
    end

    local distance = getDistanceBetweenPoints2D(pointX, pointY, shortestX, shortestY)

    return distance
end
```

</section>
Example
-------

<section name="Client" class="client" show="true">
This code draws a red line, enables mouse cursor and tells client how far from the line was clicked.

``` lua
-- Draw a red line
addEventHandler("onClientRender", getRootElement(),
    function()
        dxDrawLine(20, 20, 200, 100, tocolor(255, 0, 0))
    end
)

-- Show cursor
showCursor(true)

-- Fires when left mouse button is clicked
function cursorPositionFromTheRedLine(button, state, clickedX, clickedY)
    -- Allow function to continue only if left button was pressed and button was pressed down
    if button ~= "left" or state == "up" then
        return
    end

    -- Calculate the distance
    local distance = getDistanceBetweenPointAndSegment2D(clickedX, clickedY, 20, 20, 200, 100)

    -- Tell user the distance
    outputChatBox("You clicked "..distance.." away from the Red Line!")
end

-- Read mouse clicks
addEventHandler("onClientClick", root, cursorPositionFromTheRedLine)
```

</section>
Code from: <http://www.allegro.cc/forums/thread/589720>

See Also
--------
