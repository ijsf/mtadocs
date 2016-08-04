This function removes a [shader](/docs/shader.md "wikilink") from one or more world textures.

Syntax
------

``` lua
bool engineRemoveShaderFromWorldTexture ( element shader, string textureName [, element targetElement = nil ] )
```

### Required Arguments

-   **shader:** The shader which is to be removed
-   **textureName:** The name of the world texture to remove the shader from. It should be exactly the same string as used with [engineApplyShaderToWorldTexture](/docs/engineapplyshadertoworldtexture.md "wikilink") when the shader was initially applied.

### Optional Arguments

### Returns

Returns *true* if the shader was successfully removed, *false* otherwise.

Example
-------

This example will remove a previously created shader from the “des\_logwall” world texture

``` lua
engineRemoveShaderFromWorldTexture ( myShader, "des_logwall" )
```

Changelog
---------

See Also
--------
