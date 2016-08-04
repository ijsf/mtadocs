This function applies a [shader](/docs/shader.md "wikilink") to one or more world textures.

Syntax
------

``` lua
bool engineApplyShaderToWorldTexture ( element shader, string textureName [, element targetElement = nil, bool appendLayers = true ] )
```

### Required Arguments

-   **shader:** The shader which is to be applied
-   **textureName:** The name of the world texture to apply the shader to. Wildcard matching e.g. “ro?ds\*” can be used to apply to more than one texture at a time.

### Optional Arguments

-   **appendLayers:** allows two or more layered shaders to be applied in the same texture. You may want to modify the *DepthBias* in the technique pass to avoid Z-fighting artifacts when using this.

### Returns

Returns *true* if the shader was successfully applied, *false* otherwise.

Example
-------

This example will apply a shader to the “des\_logwall” world texture (which is used by the house near the 'play' gamemode spawn point)

``` lua
myShader = dxCreateShader( "hello.fx" )
engineApplyShaderToWorldTexture( myShader, "des_logwall" )
```

This untested example will apply a shader to the current vehicle of the local player

``` lua
myShader = dxCreateShader( "hello.fx" )

addEventHandler("onClientVehicleEnter", root,
    function(thePlayer, seat)
        local theVehicle = source
        if seat == 0 and thePlayer == localPlayer then
            engineApplyShaderToWorldTexture( myShader, "vehiclegrunge256", theVehicle )
            engineApplyShaderToWorldTexture( myShader, "?emap*", theVehicle )
        end
    end
)

addEventHandler("onClientVehicleExit", root,
    function(thePlayer, seat)
        local theVehicle = source
        if seat == 0 and thePlayer == localPlayer then
            engineRemoveShaderFromWorldTexture( myShader, "vehiclegrunge256", theVehicle )
            engineRemoveShaderFromWorldTexture( myShader, "?emap*", theVehicle )
        end
    end
)
```

Changelog
---------

See Also
--------
