This function changes the water color of the GTA world.

Syntax
------

``` lua
bool setWaterColor ( int red, int green, int blue, [ int alpha = 200 ] )
```

### Required Arguments

-   **red:** The *red* value of the water, from 0 to 255.
-   **green:** The *green* value of the water, from 0 to 255.
-   **blue:** The *blue* value of the water, from 0 to 255.

### Optional Arguments

-   **alpha:** The *alpha* (visibility) value of the water, from 0 to 255. Defaults to 200 if not declared.

### Returns

Returns *true* if water color was set correctly, *false* if invalid values were passed.

Example
-------

This example adds a command *watercolor* with which a player can change the water colour.

``` lua
function changeWaterColor ( commandName, red, green, blue, alpha )
    -- if alpha is input, then include it too
    alpha = tonumber ( alpha ) or 200
    red = tonumber ( red )
    green = tonumber ( green )
    blue = tonumber ( blue )
    -- check if the colour values for red, green and blue are valid
    if red and green and blue then
        setWaterColor ( red, green, blue, alpha )
    else
        outputChatBox ( "Failed to change the water colour!" )
    end
end
addCommandHandler ( "watercolor", changeWaterColor )
```

See Also
--------
