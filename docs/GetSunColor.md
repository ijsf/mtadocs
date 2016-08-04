This function is used to get the color of the sun.

Syntax
------

``` lua
int, int, int, int, int, int getSunColor ( )
```

### Returns

Returns the color of the sun as six numbers, false if its default.

Example
-------

This example lets any player get the color of the sun like /getsuncolor

``` lua
function commandGetSunColor(player, command)
    local Ra, Ga, Ba, Rb, Gb, Bb = getSunColor()
    if (Ra) then
        outputChatBox("The current color of the sun is "..Ra.." "..Ga.." "..Ba.." "..Rb.." "..Gb.." "..Bb..".", player, 0, 255, 0)
    else
        outputChatBox("The color of the sun is normal.", player, 0, 255, 0)
    end
end
addCommandHandler("getsuncolor", commandGetSunColor)
```

See Also
--------
