This function is used to set the color of the sun.

Syntax
------

``` lua
bool setSunColor ( int aRed, int aGreen, int aBlue, int bRed, int bGreen, int bBlue  )
```

### Required Arguments

-   **aRed:** The amount of red (0-255) you want the sun to be.
-   **aGreen:** The amount of green (0-255) you want the sun to be.
-   **aBlue:** The amount of blue (0-255) you want the sun to be.
-   **bRed:** The amount of red (0-255) you want the sun to be.
-   **bGreen:** The amount of green (0-255) you want the sun to be.
-   **bBlue:** The amount of blue (0-255) you want the sun to be.

### Returns

Returns true if the color of the sun was set, false otherwise.

Example
-------

This example lets any player set the color of the sun like /setsuncolor 255 0 0

``` lua
function commandSetSunColor(player, command, r, g, b, r2, g2, b2)
    local r, g, b, r2, g2, b2 = tonumber(r), tonumber(g), tonumber(b), tonumber(r2), tonumber(g2), tonumber(b2)
    if (r and g and b and r2 and g2 and b2) then
        setSunColor(r, g, b, r2, g2, b2)
        outputChatBox("Color of sun now set", player, 0, 255, 0)
    else
        outputChatBox("Usage: /setsuncolor r g b r2 g2 b2 (eg: /setsuncolor 255 0 0 255 0 0)", player, 255, 0, 0)
    end
end
addCommandHandler("setsuncolor", commandSetSunColor)
```

See Also
--------
