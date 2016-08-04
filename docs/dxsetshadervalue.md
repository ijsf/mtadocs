This sets a named parameter for a [shader](/docs/shader.md "wikilink") element

Syntax
------

``` lua
bool dxSetShaderValue ( element theShader, string parameterName, mixed value )
```

### Required Arguments

-   **theShader:** The shader element whose parameter is to be changed
-   **parameterName:** The name of parameter
-   **value:** The value to set, which can be a [texture](/docs/texture.md "wikilink"), a bool, a number or a list of numbers

### Returns

Returns *true* if the shader element's parameter was successfully changed, *false* otherwise.

Example
-------

``` lua
myShader = dxCreateShader( "hello.fx" )
myTexture = dxCreateTexture( "man.png" )
dxSetShaderValue( myShader, "texure0", myTexture )                -- Set a texture
dxSetShaderValue( myShader, "bShowThing", true )                  -- Set a bool                  
dxSetShaderValue( myShader, "speed", 2.4 )                        -- Set a number
dxSetShaderValue( myShader, "positionOfCheese", 100, 200, 300 )   -- Set a list of numbers
```

See Also
--------
