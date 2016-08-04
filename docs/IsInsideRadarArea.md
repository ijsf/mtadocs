This function checks if a 2D position is inside a [radar area](/radararea.md "wikilink") or not.

Syntax
------

``` lua
bool isInsideRadarArea ( radararea theArea, float posX, float posY )
```

### Required Arguments

-   **theArea:** The [radar area](/radararea.md "wikilink") you're checking the position against.
-   **posX:** The X coordinate of the position you're checking.
-   **posY:** The Y coordinate of the position you're checking.

### Returns

Returns *true* if the position is inside the radar area, *false* if it isn't or if any parameters are invalid.

Example
-------

This function checks if an element is within a radar area.

``` lua
function isElementInsideRadarArea ( theElement, theArea )
    -- get the x, y coordinates from getElementPosition (z gets silently discarded)
    local posX, posY = getElementPosition( theElement )
    -- call isInsideRadarArea with those coordinates and return its result
    return isInsideRadarArea ( theArea, posX, posY )
end
```

See Also
--------
