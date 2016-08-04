This function gets the current camera rotation of a [ped](/docs/ped.md "wikilink").

Syntax
------

``` lua
float getPedCameraRotation( ped thePed )
```

### Required Arguments

-   **thePed:** the [ped](/docs/ped.md "wikilink") to retrieve the camera rotation of.

### Returns

Returns the camera rotation of the [ped](/docs/ped.md "wikilink") in degrees if successful. Returns *false* if an invalid element was passed.

Example
-------

This example creates a **/getrotation** command which outputs the expected camera rotation of the player which types it.

``` lua
addCommandHandler( "getrotation", 
    function ()
        local rot = 360 - getPedCameraRotation(localPlayer) -- Also fix the camera rotation
        outputChatBox("Your camera rotation is " .. rotation .. "º", 0, 225 0)
    end
)
```

See Also
--------
