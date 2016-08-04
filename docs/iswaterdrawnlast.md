Syntax
------

``` lua
 bool isWaterDrawnLast ( )
```

### Returns

Returns *true* if water is drawn last in the rendering order, *false* otherwise.

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
