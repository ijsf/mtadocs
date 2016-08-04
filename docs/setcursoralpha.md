This function is used to change alpha (transparency) from the client's cursor.

Syntax
------

``` lua
bool setCursorAlpha( int alpha )
```

### Required Arguments

-   '''alpha ''': The alpha value to set. Value can be 0-255, where 255 is fully opaque and 0 is fully transparent.

### Returns

Returns *true* if the new alpha value was set, or *false* otherwise.

Requirements
------------

Example
-------

``` lua
-- Simple command to test the setCursorAlpha function
addCommandHandler( "cursorAlpha", 
    function ()
        -- Show the cursor if it is not showing or hide the cursor if it is
        showCursor( not isCursorShowing ( ) )
        -- Set the alpha to 100
        setCursorAlpha(100)
    end
)
```

See Also
--------
