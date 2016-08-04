This function will tell you what color a blip is. This color is only applicable to the default blip icon ([12px](/docs/image:blipid0s.png.md "wikilink"), [12px](/docs/image:blipid0u.png.md "wikilink") or [12px](/docs/image:blipid0d.png.md "wikilink")). All other icons will ignore this.

Syntax
------

``` lua
int int int int getBlipColor ( blip theBlip )
```

### Required Arguments

-   **theBlip:** The blip whose color you wish to get.

### Returns

Returns four integers in RGBA format, with a maximum value of 255 for each. The values are, in order, *red*, *green*, *blue*, and *alpha*. Alpha decides the transparancy where 255 is opaque and 0 is fully transparent. *false* is returned if the blip is invalid.

Example
-------

This example will find all the blips that exist and set them all to white if they aren't white already.

``` lua
-- Retrieve a table containing all the blips that exist
blips = getElementsByType ( "blip" )
-- Loop through the list, storing the blip from the table in the variable blipValue
for blipKey, blipValue in ipairs(blips) do
    -- Retrieve the blip's colors into the variables red, green, blue and alpha
    red, green, blue, alpha = getBlipColor ( blipValue )
    -- If the blip's icon isn't white already
    if ( red ~= 255 or green ~= 255 or blue ~= 255 or alpha ~= 255 ) then
        -- Set the blip's color to white
        setBlipColor ( blipValue, 255, 255, 255, 255 )
    end
end
```

See Also
--------
