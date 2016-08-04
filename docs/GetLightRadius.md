Syntax
------

``` lua
float getLightRadius ( light theLight )
```

### Required Arguments

-   **theLight:** The [light](/Element/Light.md "wikilink") that you wish to retrieve the radius of.

### Returns

Returns a [float](/float.md "wikilink") containing the radius of the specified light, *false* if invalid arguments were passed.

### Example

``` Lua
local light = createLight(0, 0, 0, 4)
outputChatBox("light radius: " .. getLightRadius(light))
```

See also
--------
