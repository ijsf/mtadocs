This function sets the current position of the mouse cursor.

Syntax
------

``` lua
bool setCursorPosition (int cursorX, int cursorY )
```

### Required Arguments

-   **cursorX:** Position over the X axis
-   **cursorY:** Position over the Y axis

### Returns

Returns *true* if the position has been successfully set, *false* otherwise.

Example
-------

This example sets your cursor position to the center of your screen after using the command *cursorpos*.

``` lua
function centerCursorFunction()
    local showing = isCursorShowing ()
    if showing then -- if the cursor is showing
        local screenX, screenY = guiGetScreenSize () --get the screen size in pixels
        setCursorPosition (screenX/2, screenY/2) --set the cursor position to the center of the screen
    else
        outputChatBox( "Your cursor is not showing." )
    end
end
addCommandHandler( "centerCursor", centerCursorFunction )
```

Issues
------

See Also
--------
