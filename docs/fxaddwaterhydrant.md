[thumb|200px|Water hydrant](/docs/Image:Fxwaterhydrant.png.md "wikilink") This function creates a water hydrant particle effect.

Syntax
------

``` lua
bool fxAddWaterHydrant ( float posX, float posY, float posZ )
```

### Required Arguments

-   **posX:** A float representing the **x** position of the hydrant
-   **posY:** A float representing the **y** position of the hydrant
-   **posZ:** A float representing the **z** position of the hydrant

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

This example will create 20 water hydrant effects around the players position when they use the command: hydrantmania.

``` lua
function createHydrants()
    local x, y, z = getElementPosition(localPlayer) -- Get your location.
    for i=0, 20 do -- 20 Hydrants.
        fxAddWaterHydrant(x + math.random(-5,5), y + math.random(-5,5), z) -- Using math.random, and your current location 20 water hydrants are created.
    end
end
addCommandHandler("hydrantmania", createHydrants)
```

See Also
--------
