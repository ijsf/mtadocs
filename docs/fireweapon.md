Fires one shot from a [custom weapon](/docs/Element/Weapon.md "wikilink").

Syntax
------

``` lua
bool fireWeapon ( weapon theWeapon )
```

### Required Arguments

-   **theWeapon:** The weapon to be fired.

### Returns

Returns *true* if the shot weapon is valid and therefore the shot was fired, *false* otherwise.

Example
-------

This function creates and fires a weapon.

``` lua
function createAndFire()
    local weapon = createWeapon("mp5", 0, 0, 3) -- Create a MP5 at the coordinates 0, 0, 3
    fireWeapon(weapon) -- Fire the weapon we spawned
end
addEventHandler("onClientResourceStart", resourceRoot, createAndFire)
```

Requirements
------------

See also
--------
