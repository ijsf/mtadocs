Syntax
------

``` lua
searchlight setSearchLightStartPosition ( searchlight theSearchLight, float startX, float startY, float startZ )
```

### Required Arguments

-   **theSearchLight**: the searchlight to modify the property of.
-   **startX**: the X coordinate where the searchlight light cone will start.
-   **startY**: the Y coordinate where the searchlight light cone will start.
-   **startZ**: the Z coordinate where the searchlight light cone will start.

### Returns

If every argument is correct, this function returns *true*. If not, it will return *false* plus an error message.

Example
-------

This example creates a searchlight that originates in the camera position and targets the center of the map.

``` lua
local searchLight = createSearchLight(0, 0, 0, 0, 0, 0, 0, 10)

if searchLight then
    local function updateSearchLight()
        -- Set its start position to the camera position
        setSearchLightStartPosition(searchLight, getCameraMatrix())
    end
    addEventHandler("onClientPreRender", root, updateSearchLight)
end
```

See also
--------
