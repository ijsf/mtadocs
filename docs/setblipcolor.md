This function will let you change the color of a blip. This color is only applicable to the default blip icon ([12px](/docs/image-blipid0s.png.md "wikilink"), [12px](/docs/image-blipid0u.png.md "wikilink") or [12px](/docs/image-blipid0d.png.md "wikilink")). All other icons will ignore this.

Syntax
------

``` lua
bool setBlipColor ( blip theBlip, int red, int green, int blue, int alpha )
```

### Required Arguments

-   **theBlip:** The blip who's color you wish to set.
-   **red:** The amount of red in the blip's color (0 - 255).
-   **green:** The amount of green in the blip's color (0 - 255).
-   **blue:** The amount of blue in the blip's color (0 - 255).
-   **alpha:** The amount of alpha in the blip's color (0 - 255). Alpha decides transparancy where 255 is opaque and 0 is transparent.

### Returns

Returns *true* if the blip's color was set successfully. Returns *false* if the blip passed to the function is invalid, or any of the colors are out of the valid range.

Example
-------

This example will find all the blips that exist and set them all to white if they aren't white already.

``` lua
-- Retrieve a table containing all the blips that exist
local blips = getElementsByType ( "blip" )
-- Loop through the list, storing the blip from the table in the variable blipValue
for blipKey, blipValue in ipairs ( blips ) do
    -- Retrieve the blip's colors into the variables red, green, blue and alpha
    local red, green, blue, alpha = getBlipColor ( blipValue )
    -- If the blip's icon isn't white already
    if ( red ~= 255 or green ~= 255 or blue ~= 255 or alpha ~= 255 ) then
        -- Set the blip's color to white
        setBlipColor ( blipValue, 255, 255, 255, 255 )
    end
end
```

See Also
--------
