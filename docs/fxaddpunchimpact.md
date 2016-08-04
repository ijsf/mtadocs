[thumb|200px|Punch impact](/docs/image:fxpunchimpact.png.md "wikilink") Creates a punch impact particle effect (a small dust cloud).

Syntax
------

``` lua
bool fxAddPunchImpact ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the effect originates.
-   **dirX, dirY, dirZ:** a vector indicating the movement direction of the effect.

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Punch Impact Effect next to you when typing */pimpact* in the Chatbox.

``` lua
addCommandHandler("pimpact", function()
    local x, y, z = getElementPosition(localPlayer)
    local gz = getGroundPosition(x, y, z)
    fxAddPunchImpact(x, y, gz, 0, 0, 0)
end)
```

</section>
See Also
--------
