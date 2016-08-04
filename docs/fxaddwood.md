[thumb|200px|Wood](/docs/image:fxwood.png.md "wikilink") Creates a wood splinter particle effect.

Syntax
------

``` lua
bool fxAddWood ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ, [int count=1, float brightness=1.0] )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the effect originates.
-   **dirX, dirY, dirZ:** a direction vector indicating where the wood splinters fly to.

### Optional Arguments

-   **count:** the number of splinters to create.
-   **brightness:** the brightness. Ranges from 0 (black) to 1 (normal color).

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Wood Effect next to you when typing */woodfx* in the Chatbox.

``` lua
addCommandHandler("woodfx", function()
    local x, y, z = getElementPosition(localPlayer)
    local gz = getGroundPosition(x, y, z)
    fxAddWood(x, y, gz+0.4, 0, 0, 0, math.random(3, 6), 0.7)
end)
```

</section>
See Also
--------
