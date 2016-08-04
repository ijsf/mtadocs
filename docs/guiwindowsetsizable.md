This function enables or disables user resizing of a GUI window.

Syntax
------

``` lua
bool guiWindowSetSizable ( element theElement, bool status )
```

### Required Arguments

-   **theElement:** The window to be changed.
-   **status:** A boolean value indicating whether user resizing is to be enabled or disabled.

### Returns

Returns *true* if the function is successful, *false* otherwise.

Example
-------

This example creates a gui window and sets it to be not sizable

``` lua
function initialize ()
    -- Create a gui window
    local window = guiCreateWindow ( 0.50, 0.50, 0.25, 0.25, "Test", true )
    -- set it to be not sizable
    guiWindowSetSizable ( window, false )
    -- Show cursor to check if our changes work fine
    showCursor ( true )
end
addEventHandler ( "onClientResourceStart", resourceRoot, initialize )
```

See Also
--------
