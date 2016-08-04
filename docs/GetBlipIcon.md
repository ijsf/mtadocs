This function returns the icon a blip currently has.

Syntax
------

``` lua
int getBlipIcon ( blip theBlip )
```

### Required Arguments

-   **theBlip**: the blip we're getting the icon number of.

### Returns

Returns an [int](/int.md "wikilink") indicating which icon the blip has. Valid values are listed on the [Blip Icons](/Blip_Icons.md "wikilink") page.

Example
-------

This example will find all the blips that exist and set them all to the default blip icon.

``` lua
-- Retrieve a table containing all the blips that exist
blips = getElementsByType ( "blip" )
-- Loop through the list, storing the blip from the table in the variable blipValue
for blipKey, blipValue in ipairs(blips) do
    -- Retrieve the blip's icon into the variable 'blipIcon'
    blipIcon = getBlipIcon ( blipValue )
    -- If the blip's icon wasn't the default already
    if ( blipIcon ~= 0 ) then
        -- Set the blip's icon to the default
        setBlipIcon ( blipValue, 0 )
    end
end
```

See Also
--------
