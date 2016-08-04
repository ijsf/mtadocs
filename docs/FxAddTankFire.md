[thumb|200px|Tank fire](/Image:Fxtankfire.png.md "wikilink") This function creates a tank firing particle effect.

Syntax
------

``` lua
bool fxAddTankFire ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the effect originates.
-   **dirX, dirY, dirZ:** a direction vector indicating where the tank fire is directed to.

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Tank Fire Effect at your weapon's muzzle position

``` lua
addEventHandler("onClientPlayerWeaponFire", root, function(weapon, ammo, ammoInClip, hitX, hitY, hitZ, hitElement)
    if weapon == 0 then return end -- If the player is unarmed, return end.
    local mX, mY, mZ = getPedWeaponMuzzlePosition(localPlayer)
    fxAddTankFire(mX, mY, mZ, 0, 90, 0)
end)
```

</section>
See Also
--------
