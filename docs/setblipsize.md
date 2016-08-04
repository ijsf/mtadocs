This function sets the size of a blip's icon.

Syntax
------

``` lua
bool setBlipSize ( blip theBlip, int iconSize )
```

### Required Arguments

-   **theBlip:** The blip you wish to get the size of.
-   **iconSize:** The size you wish the icon to be. 2 is the default value.

### Returns

Returns an *true* if the blip's size was set successfully. Returns *false* if the [element](/docs/element.md "wikilink") passed was not a [blip](/docs/blip.md "wikilink") or if the icon size passed was invalid.

Example
-------

This example will reset the size of all blips to the default.

``` lua
-- Retrieve a table containing all the blips that exist
blips = getElementsByType ( "blip" )
-- Loop through the list
for blipKey, blipValue in ipairs(blips) do
    -- Retrieve the blip's size into the variable 'blipSize'
    blipSize = getBlipSize ( blipValue )
    -- If the blip's size wasn't 2 (the default size) already
    if ( blipSize ~= 2 ) then
        -- Set the size to the default
        setBlipSize ( blipValue, 2 )
    end
end
```

See Also
--------
