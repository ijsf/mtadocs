[thumb|200px|Water splash](/Image:Fxwatersplash.png.md "wikilink") This function creates a water splash particle effect.

Syntax
------

``` lua
bool fxAddWaterSplash ( float posX, float posY, float posZ )
```

### Required Arguments

-   **posX:** A float representing the **x** position of the splash
-   **posY:** A float representing the **y** position of the splash
-   **posZ:** A float representing the **z** position of the splash

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Water Splash at the position of the bullet impact whenever you shoot.

``` lua
addEventHandler("onClientPlayerWeaponFire", root, function(weapon, ammo, ammoInClip, hitX, hitY, hitZ, hitElement)
    if weapon == 0 then return end -- If the player is unarmed, return end.
    fxAddWaterSplash(hitX, hitY, hitZ)
end)
```

</section>
See Also
--------
