[thumb|200px|Tyre burst](/Image:Fxtyreburst.png.md "wikilink") Creates a tyre burst particle effect (a small white smoke puff).

Syntax
------

``` lua
bool fxAddTyreBurst ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the puff originates.
-   **dirX, dirY, dirZ:** a vector indicating the movement direction of the effect.

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Tyre Burst Effect next to you when typing */tyreburst* in the Chatbox.

``` lua
addCommandHandler("tyreburst", function()
    local x, y, z = getElementPosition(localPlayer)
    local gz = getGroundPosition(x, y, z)
    fxAddTyreBurst(x, y, gz, 0, 0, 0)
end)
```

</section>
See Also
--------
