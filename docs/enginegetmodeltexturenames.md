This function returns a table of the world textures which are applied to the specified model.

Syntax
------

``` lua
table engineGetModelTextureNames( string modelId = "" )
```

### Required Arguments

-   **modelId :** You can either use the model id or the model name.

### Returns

Returns a table if this function succeeds, false if it fails for some reason.

Example
-------

This example will output the texture names applied to the Comet.

``` lua
for _,name in ipairs( engineGetModelTextureNames( "480" ) ) do
    outputConsole( name )
end
```

The model name can also be used.

``` lua
for _,name in ipairs( engineGetModelTextureNames( "Comet" ) ) do
    outputConsole( name )
end
```

See Also
--------
