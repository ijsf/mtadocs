This function returns a list of the world textures which are being used to draw the current scene.

Syntax
------

``` lua
table engineGetVisibleTextureNames ( [ string nameFilter = "*", string modelId = "" ] )
```

### Optional Arguments

-   **nameFilter:** Only include textures that match the wildcard string.
-   **modelId :** Only include textures that are used by the model id (or model name)

### Returns

Returns a table of texture names.

Example
-------

This example will output the names of all the visible textures that start with 'a'

``` lua
for _,name in ipairs( engineGetVisibleTextureNames ( "a*" ) ) do
    outputConsole( name )
end
```

See Also
--------
