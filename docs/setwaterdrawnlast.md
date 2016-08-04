Syntax
------

``` lua
bool setWaterDrawnLast ( bool bEnabled )
```

### Required Arguments

-   **bEnabled**: A boolean value determining whether water should be drawn last.

### Returns

Returns *true* if the rendering order was changed successfully, *false* otherwise.

Example
-------

This example toggles water to be drawn last.

``` lua
function toggleWaterDrawnLast ()
    local bWaterDrawnLast = not isWaterDrawnLast()
    outputChatBox (string.format('setWaterDrawnLast: %s', tostring(bWaterDrawnLast)))
    return setWaterDrawnLast (bWaterDrawnLast)
end
addCommandHandler ('togglewater', toggleWaterDrawnLast)
```

Requirements
------------

See Also
--------
