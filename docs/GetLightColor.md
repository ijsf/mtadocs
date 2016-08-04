Syntax
------

``` lua
int, int, int getLightColor ( light theLight )
```

### Required Arguments

-   **theLight:** The [light](/docs/Element/Light.md "wikilink") that you wish to retrieve the color of.

### Returns

Returns three [ints](/docs/int.md "wikilink") corresponding to the amount of red, green and blue (respectively) of the light, *false* if invalid arguments were passed.

### Example

``` Lua
local light = createLight(0, 0, 0, 4)
local red, green, blue = getLightColor(light)
outputChatBox(" light color is " .. red .. ", " .. green .. ", " .. blue)
```

See also
--------
