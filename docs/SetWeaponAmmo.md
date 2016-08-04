<section name="setWeaponAmmo" class="server" show="true">
Sets the ammo to a certain amount for a specified weapon (if they already have it), regardless of current ammo.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **thePlayer:** A [player](/player.md "wikilink") object referencing the specified player
-   **weapon:** A whole number integer that refers to a [weapon](/weapon.md "wikilink") ID.
-   **totalAmmo:** A whole number integer serving as the total ammo amount for the given weapon (including ammo in clip).

### Optional Arguments

-   **ammoInClip:** The amount of ammo to set in the player's clip. This will be taken from the main ammo. If left unspecified or set to 0, the current clip will remain.

Returns
-------

Returns a boolean value *true* or *false* that tells you if it was successful or not.

Example
-------

``` lua
local randPlayer = getRandomPlayer() -- Get a random player
giveWeapon(randPlayer,35,100) -- Give them a rocket launcher with 100 rockets.
setWeaponAmmo(randPlayer,35,50) -- Decide we're only going to give them 50 rockets.
```

</section>
<section name="setWeaponAmmo (custom weapons)" class="client" show="true">
Set the ammo of a custom weapon which was created through [createWeapon](/createWeapon.md "wikilink"). By default, a custom weapon has 9999 ammo (which means infinite ammo).

Syntax
------

``` lua
bool setWeaponAmmo ( weapon theWeapon, int ammo )
```

### Required arguments

-   **theWeapon:** The weapon to set the ammo of.
-   **ammo:** The total ammo amount for the given weapon (including ammo in clip).

Returns
-------

Returns *true* on success, *false* otherwise.

Example
-------

``` lua
local weapon = createWeapon ("deagle",0, 0, 10) -- Create the weapon
setWeaponAmmo(weapon,5000) 
```

</section>
Requirements
------------

</section>
See also
--------

[ru:setWeaponAmmo](/ru:setWeaponAmmo.md "wikilink")
