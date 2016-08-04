[thumb|200px|Bullet splash](/docs/image:fxbulletsplash.png.md "wikilink") This function creates a bullet splash particle effect, normally created when shooting into water.

Syntax
------

``` lua
bool fxAddBulletSplash ( float posX, float posY, float posZ )
```

### Required Arguments

-   **posX:** A float representing the **x** position of the splash
-   **posY:** A float representing the **y** position of the splash
-   **posZ:** A float representing the **z** position of the splash

### Returns

Returns a true if the operation was successful, false otherwise.

### Example

<section name="Client" class="client" show="true">
This example will add a Bullet Splash Effect next to your player when typing */bsplash* in the Chatbox.

``` lua
addCommandHandler("bsplash", function()
    local x, y, z = getElementPosition(localPlayer)
    local gz = getGroundPosition(x, y, z)
    fxAddBulletSplash(x, y, gz)
end)
```

</section>
See Also
--------
