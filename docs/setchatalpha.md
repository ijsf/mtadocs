This function sets the global alpha value of the in-game chat. The alpha value applies to text output, input line and background colors.

Syntax
------

``` lua
bool setChatAlpha ( float alpha )
```

### Required Arguments

-   **alpha:** the new global alpha value for the in-game chat (0-255)

### Returns

Returns *true* if alpha is a number and resides in a valid range (0-255), *false* if alpha is not a number or resides in an invalid range (like 9001).

Example
-------

This example makes everybodies chatbox flash in 1 second intervals.

``` lua
local startTime = getTickCount()
local interval = 1000 -- time in milliseconds
local baseAlpha = 200 -- the alpha value the chat will at least have
                      -- valid: 0 - 255

addEventHandler( "onClientRender", root,
    function()
        local elapsedTime = getTickCount() - startTime
        local modAlpha = ( 255 - baseAlpha ) / 2
        local alpha = math.sin( elapsedTime / interval * math.pi * 2 ) * modAlpha
                      + baseAlpha + modAlpha
                      
        setChatAlpha( alpha )
    end
)
```

Issues
------

See Also
--------
