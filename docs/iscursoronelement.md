This function checks whether the cursor in a particular area is

Function
--------

``` lua
function isCursorOnElement(x,y,w,h)
    local mx,my = getCursorPosition ()
    local fullx,fully = guiGetScreenSize()
    cursorx,cursory = mx*fullx,my*fully
    if cursorx > x and cursorx < x + w and cursory > y and cursory < y + h then
        return true
    else
        return false
    end
end
```

Syntax
------

``` lua
bool isCursorOnElement( int x, int y, int width, int height )
```

### Required Arguments

-   **x**: The X absolute position at the Screen.
-   **y**: The Y absoulte position at the Screen.
-   **width**: The absolute width of the Area.
-   **height**: The absolute height of the Area.

Author: Nevo

See Also
--------
