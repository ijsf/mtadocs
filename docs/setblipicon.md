This function sets the icon for an existing blip element.

Syntax
------

``` lua
bool setBlipIcon ( blip theBlip, int icon )
```

### Required Arguments

-   **theBlip** The blip you wish to set the icon of.
-   **icon:** A number indicating the icon you wish to change it do. Valid values are listed on the [Blip Icons](/docs/blip_icons.md "wikilink") page.

### Returns

Returns *true* if the icon was successfully set, *false* if the element passed was not a valid blip or the icon value was not a valid icon number.

Example
-------

This example resets all blip icons to the default blip icon, 0.

``` lua
-- Retrieve a table containing all the blips that exist
blips = getElementsByType ( "blip" )
-- Loop through the list, storing the blip from the table in the variable blipValue
for blipKey, blipValue in blips do
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
