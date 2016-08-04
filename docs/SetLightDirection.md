Syntax
------

``` lua
bool setLightDirection ( light theLight, float x, float y, float z )
```

### Required Arguments

-   **theLight:** The [light](/Element/Light.md "wikilink") that you wish to set the direction of.

### Returns

Returns *true* if the function was successful, *false* otherwise.

### Example

``` Lua
local light = createLight(0, 0, 0, 4)
addCommandHandler("setdirectionoflight",
    function(cmd, x, y, z)
        if x and y and z then
            setLightDirection(light, tonumber(x), tonumber(y), tonumber(z))
        end
    end
)
```

See also
--------
