This function is used to reset the size of the sun to its normal size.

Syntax
------

``` lua
bool resetSunSize ( )
```

### Returns

Returns true if the size of the sun was reset, false otherwise.

Example
-------

This example lets any player reset the size of the sun like /resetsunsize

``` lua
function commandResetSunSize(player, command)
    resetSunSize()
end
addCommandHandler("resetsunsize", commandResetSunSize)
```

See Also
--------
