[thumb|200px|Debris](/docs/image-fxdebris.png.md "wikilink") Creates a debris particle effect (e.g. bits that fly off a car when ramming a wall).

Syntax
------

``` lua
bool fxAddDebris ( float posX, float posY, float posZ, [int colorR=255, int colorG=0, int colorB=0, int colorA=255, float scale=1.0, int count=1] )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the debris originates.

### Optional Arguments

-   **colorR, colorG, colorB, colorA:** the color and alpha (transparency) of the debris effect.
-   **scale:** the size of the chunks.
-   **count:** the number of chunks to create.

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Debris Effect next to you when typing */debris* in the Chatbox.

``` lua
addCommandHandler("debris", function()
    local x, y, z = getElementPosition(localPlayer)
    local randomColor, randomAmount = math.random(0, 255), math.random(4, 8)
    fxAddDebris(x, y, z, randomColor, randomColor, randomColor, 255, 1.0, randomAmount)
end)
```

</section>
See Also
--------
