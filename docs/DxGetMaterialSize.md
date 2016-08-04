This gets the dimensions of the supplied [material](/material.md "wikilink") element.

Syntax
------

``` lua
int, int [, int] dxGetMaterialSize ( element material )
```

### Required Arguments

-   **material :** The material element whose size is to be gotten

### Returns

Returns two *ints* representing the width and height in pixels of the material, or false if an invalid parameter was passed to the function. If the material is a volume texture, this function will return three *ints* representing the width, height and depth.

Example
-------

``` lua
myTexture = dxCreateTexture( "man.png" )
local width, height = dxGetMaterialSize( myTexture )
outputChatBox( "man.png is " .. tostring(width) .. " pixels wide and " .. tostring(height) .. " pixels high" )
```

Changelog
---------

See Also
--------
