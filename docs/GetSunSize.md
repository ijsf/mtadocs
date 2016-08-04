This function is used to get the size of the sun.

Syntax
------

``` lua
float getSunSize ( )
```

### Returns

Returns the size of the sun as a number, false if the size of the sun is at its default.

Example
-------

This example lets any player get the size of the sun like /getsunsize

``` lua
function commandGetSunSize(player, command)
    local size = getSunSize()
    if (size) then
        outputChatBox("The current size of the sun is "..size..".", player, 0, 255, 0)
    else
        outputChatBox("The size of the sun is normal.", player, 0, 255, 0)
    end
end
addCommandHandler("getsunsize", commandGetSunSize)
```

See Also
--------
