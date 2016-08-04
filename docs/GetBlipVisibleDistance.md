This function will tell you what visible distance a blip has.

Syntax
------

``` lua
float getBlipVisibleDistance ( blip theBlip )
```

### Required Arguments

-   **theBlip:** The blip whose visible distance you wish to get.

### Returns

Returns one float with the blips visible distance, false if the blip is invalid.

Example
-------

This example will demonstrate basic functionality of getBlipVisibleDistance

``` lua
local blip = createBlip(0, 0, 0, 47, 0, 0, 0, 0, 0, 0, 1000)
outputDebugString("Blip visible distance: "..getBlipVisibleDistance(blip))
```

This example will combine the total visible distances of all blips

``` lua
-- Retrieve a table containing all the blips that exist
local blips = getElementsByType("blip")
local distance = 0
-- Loop through the list, storing the blips visible distance with the rest.
for index, blip in ipairs(blips) do
    -- Retrieve the blip's visible distance
    distance = distance + getBlipVisibleDistance(blip) or 0 -- "or 0" just incase its false ;)
end
outputDebugString("Combined total of all blips visible distances: "..distance)
```

See Also
--------
