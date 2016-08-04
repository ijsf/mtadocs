This function is used to get alpha (transparency) from the client's cursor.

Syntax
------

``` lua
int getCursorAlpha ( )
```

### Returns

Returns a int, 0-255, where 255 is fully opaque and 0 is fully transparent.

Requirements
------------

Example
-------

``` lua
-- Simple command to test the getCursorAlpha function
addCommandHandler( "cursorAlpha", 
    function ()
        if ( isCursorShowing ( ) ) then
            outputChatBox( "The cursor alpha: "..getCursorAlpha( ) )
        else
            outputChatBox( "The cursor is not showing!" )
        end
    end
)
```

See Also
--------
