Sets the color of an existing radar area.

Syntax
------

``` lua
bool setRadarAreaColor ( radararea theRadarArea, int r, int g, int b, int a )               
```

### Required Arguments

-   **theRadarArea:** the radararea element whose color you wish to set.
-   **r:** an integer representing the amount of red in the color (0 for no red, 255 for solid red)
-   **g:** an integer representing the amount of green in the color (0 for no green, 255 for solid green)
-   **b:** an integer representing the amount of blue in the color (0 for no blue, 255 for solid blue)
-   **a:** an integer representing the color's alpha (0 for transparent, 255 for opaque)

### Returns

Returns *true* if the color was set successfully, *false* if the radar area doesn't exist or the color arguments are improper.

Example
-------

This example creates a radar area and changes its color right away:

``` lua
someArea = createRadarArea ( 1024, 1024, 75, 100, 0, 0, 0, 255 ) -- create a black radar area
local flag = setRadarAreaColor ( someArea, 255, 85, 85, 170 )    -- change its color
if ( flag ) then                                                 -- if the function returned true...
   outputChatBox ( "Color set successfully!" )
else                                                             -- if the function returned false...
   outputChatBox ( "Failed to set color." )
end
```

See Also
--------
