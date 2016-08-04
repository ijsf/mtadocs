This function is used for getting the X and Y size of an existing [radar area](/docs/radararea.md "wikilink").

Syntax
------

``` lua
float, float getRadarAreaSize ( radararea theRadararea )              
```

### Required Arguments

-   **theRadararea:** The [radar area](/docs/radararea.md "wikilink") element whose size you wish to get.

### Returns

Returns two *floats* indicating the X and Y length of the radar area respectively, *false* if the radar area is invalid.

Example
-------

The following example looks for radar areas whose size is smaller than 100 by 100:

``` lua
local radarareas = getElementsByType ( "radararea" ) -- get a table of radararea elements
for k, theArea in ipairs(radarareas) do -- use a generic for loop to step through each of the elements
   local sizeX, sizeY = getRadarAreaSize ( theArea ) -- get the size of the radar area
   if ( sizeX < 100 and sizeY < 100 ) then -- check if it's smaller than 100 by 100
      outputChatBox ( "A small radar area was found!" )
   end
end
```

See Also
--------
