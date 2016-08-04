Syntax
------

``` lua
int getLightType ( light theLight )
```

### Required Arguments

-   **theLight:** The [light](/Element/Light.md "wikilink") that you wish to retrieve the type of.

### Returns

Returns an [int](/int.md "wikilink") containing the type of the specified light, *false* if invalid arguments were passed.

### Example

``` Lua
local light = createLight(1, 2, 3, 4)
outputChatBox("light type " .. getLightType(light))
```

See also
--------
