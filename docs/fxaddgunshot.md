[thumb|200px|Gunshot](/docs/Image:Fxgunshot.png.md "wikilink") This function creates a gunshot particle effect.

Syntax
------

``` lua
bool fxAddGunshot ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ, [bool includeSparks=true] )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the effect originates.
-   **dirX, dirY, dirZ:** a direction vector indicating where the bullet is fired.

### Optional Arguments

-   **includeSparks:** A bool representing whether the particle effect will generate sparks.

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example adds a gunshot with sparks in front of your face.

``` lua
addCommandHandler("sshot", function()
    local x, y, z = getElementPosition(localPlayer)
    fxAddGunshot(x, y+0.5, z+0.5, 0, 0, 0, true)
end)
```

</section>
See Also
--------
