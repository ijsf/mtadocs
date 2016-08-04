This function creates a [shader](/docs/shader.md "wikilink") element that can be used in the dxDraw functions. Successful shader creation is not guaranteed unless the [Effect File](/shader.md "wikilink") contains a fallback technique which will work on every PC in the universe.

<h5>
It is highly recommended that [dxSetTestMode](/docs/dxSetTestMode.md "wikilink") is used when writing and testing scripts using dxCreateShader.

</h5>
Syntax
------

``` lua
element, string dxCreateShader ( string filepath [, float priority = 0, float maxDistance = 0, bool layered = false, string elementTypes = "world,vehicle,object,other" ] )
```

### Required Arguments

-   **filepath:** The filepath of the [shader Effect File](/docs/shader.md "wikilink")(.fx) file

### Optional Arguments

*All the following optional arguments are only relevant when the shader is used with [engineApplyShaderToWorldTexture](/docs/engineApplyShaderToWorldTexture.md "wikilink")*

-   **priority:** If more than one shader is matched to a world texture, the shader with the highest priority will be used. If there is more than one shader with the same highest priority, the most recently created shader is used.
-   **maxDistance:** If non-zero, the shader will be applied to textures nearer than maxDistance only. This can speed up rendering, but (to look good) may require the shader to fade out it's own effect as the texture reaches maxDistance.
-   **layered:** When set to true, the shader will be drawn in a separate render pass. Several layered shaders can be drawn on the same world texture. (To avoid [Z fighting](http://en.wikipedia.org/wiki/Z-fighting) artifacts, you may have to add **DepthBias=-0.0002;** to the technique pass)
-   **elementTypes:** A comma seperated list of element types to restrict this shader to. Valid element types are:
    -   world - Textures in the GTA world
    -   ped - Player and ped textures
    -   vehicle - Vehicles textures
    -   object - Objects textures
    -   other - Element textures which are not peds, vehicles or objects
    -   all - Everything

### Returns

-   **element:** A [shader](/docs/shader.md "wikilink") element if successful, *false* if invalid arguments were passed to the function. **You should always check to see if this function has returned false.**
-   **string:** The name of the technique that will be used.

Example
-------

``` lua
addEventHandler( "onClientRender", root,
    function()
        if myShader then
            dxDrawImage( 100, 350, 300, 350, myShader )
        end
    end
)

-- Use 'toggle' command to switch shader on and off
addCommandHandler( "toggle",
    function()
        if not myShader then
            myShader = dxCreateShader( "fancything.fx" )  -- Create shader
        else        
            destroyElement( myShader )                    -- Destroy shader
            myShader = nil
        end
    end
)
```

Changelog
---------

See Also
--------
