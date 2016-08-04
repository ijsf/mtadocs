[thumb|200px|Bullet impact](/docs/image-fxbulletimpact.png.md "wikilink") Creates a bullet impact particle effect, consisting of a small smoke cloud and a number of sparks.

Syntax
------

``` lua
bool fxAddBulletImpact ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ, [int smokeSize=1, int sparkCount=1, float smokeIntensity=1.0] )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the effect originates.
-   **dirX, dirY, dirZ:** a vector indicating the direction of the effect.

### Optional Arguments

-   **smokeSize:** the size of the smoke cloud.
-   **sparkCount:** the number of sparks to create.
-   **smokeIntensity:** the amount/transparency of smoke, ranges from 0 to 1.

### Returns

Returns a true if the operation was successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will create a Bullet Impact Effect on the position of the bullet impact.

``` lua
addEventHandler("onClientPlayerWeaponFire", root, function(weapon, ammo, ammoInClip, hitX, hitY, hitZ, hitElement)
    if weapon == 0 then return end -- If the player is unarmed, return end.
    fxAddBulletImpact(hitX, hitY, hitZ, 0, 0, 0, math.random(1, 2), math.random(2, 5), 1.0)
end)
```

</section>
See Also
--------
