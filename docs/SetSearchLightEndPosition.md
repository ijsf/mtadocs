Syntax
------

``` lua
searchlight setSearchLightEndPosition ( searchlight theSearchLight, float endX, float endY, float endZ )
```

### Required Arguments

-   **theSearchLight**: the searchlight to modify the property of.
-   **endX**: the X coordinate where the searchlight light cone will end.
-   **endY**: the Y coordinate where the searchlight light cone will end.
-   **endZ**: the Z coordinate where the searchlight light cone will end.

### Returns

If every argument is correct, this function returns *true*. If not, it will return *false* plus an error message.

Example
-------

This example creates a searchlight that originates in the camera position and targets to the front of it.

``` lua
local searchLight = createSearchLight(0, 0, 0, 0, 0, 0, 0, 10)

if searchLight then
    local function updateSearchLight()
        -- Get camera position and look at point
        local sx, sy, sz, ex, ey, ez = getCameraMatrix()
        -- Set searchlight's start position to the camera position, and end position to the look at point
        setSearchLightStartPosition(searchLight, sx, sy, sz)
        setSearchLightEndPosition(searchLight, ex, ey, ez)
    end
    addEventHandler("onClientPreRender", root, updateSearchLight)
end
```

See also
--------
