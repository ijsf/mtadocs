This function will set the visible distance of a blip.

Syntax
------

``` lua
bool setBlipVisibleDistance ( blip theBlip, float theDistance )
```

### Required Arguments

-   **theBlip:** The blip whose visible distance you wish to get.
-   **theDistance:** The distance you want the blip to be visible for.

### Returns

Returns true if successful, false otherwise.

Example
-------

This example will demonstrate basic functionality of setBlipVisibleDistance

``` lua
local blip = createBlip(0, 0, 0, 47, 0, 0, 0, 0, 0, 0, 1000)
outputDebugString("Blip visible distance: "..getBlipVisibleDistance(blip)) --1000
setBlipVisibleDistance(blip, 2000)
outputDebugString("Blip visible distance: "..getBlipVisibleDistance(blip)) --2000
```

This example will set the visible distance of all blips to half the original value.

``` lua
-- Retrieve a table containing all the blips that exist
local blips = getElementsByType("blip")
-- Loop through the list, storing the blips visible distance with the rest.
for index, blip in ipairs(blips) do
    -- Retrieve the blip's visible distance and divide by 2
    setBlipVisibleDistance(blip, getBlipVisibleDistance(blip) / 2)
end
```

See Also
--------
