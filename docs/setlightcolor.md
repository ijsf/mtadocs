Syntax
------

``` lua
bool setLightColor ( light theLight, float r, float g, float b )
```

### Required Arguments

-   **theLight:** The [light](/docs/Element/Light.md "wikilink") that you wish to set the color of.

### Returns

Returns *true* if the function was successful, *false* otherwise.

### Example

``` Lua
local light = createLight(1, 2, 3, 4)
addCommandHandler("setcoloroflight",
    function(cmd, r, g, b)
        if r and g and b then
            setLightColor(light, tonumber(r), tonumber(g), tonumber(b))
               end
    end
)
```

See also
--------
