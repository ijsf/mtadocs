This function can be used to retrieve the current color of a [radar area](/radararea.md "wikilink").

Syntax
------

``` lua
int, int, int, int getRadarAreaColor ( radararea theRadararea )              
```

### Required Arguments

-   **theRadararea:** The [radar area](/radararea.md "wikilink") you wish to retrieve the colour of.

### Returns

Returns four integers in RGBA format (*red*, *green*, *blue*, *alpha*), with a maximum value of 255 for each. Alpha decides transparency where 255 is opaque and 0 is transparent. Returns *false* if the radararea is invalid.

Example
-------

This example checks the color of a radararea defined as 'area' and announces if it is Ballas or Grove Street territory.

``` lua
local r,g,b,a = getRadarAreaColor ( area )           -- get the color of 'area' and store it in 'r', 'g', 'b' and 'a'
if r == 0 and g == 255 and b == 0 then               -- if the radar area is fully green
    outputChatBox ( "This is Grove Street turf!" )   -- announce it as grove street area
elseif r == 255 and g == 0 and b == 255 then         -- if it is purple however
    outputChatBox ( "This is Ballas turf!" )         -- announce it as ballas area
end
```

See Also
--------
