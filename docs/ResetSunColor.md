This function is used to reset the color of the sun to its normal color.

Syntax
------

``` lua
bool resetSunColor ( )
```

### Returns

Returns true if the color of the sun was reset, false otherwise.

Example
-------

This example lets any player reset the color of the sun like /resetsuncolor

``` lua
function commandResetSunColor(player, command)
    resetSunColor()
end
addCommandHandler("resetsuncolor", commandResetSunColor)
```

See Also
--------
