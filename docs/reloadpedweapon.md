This function makes a pedestrian reload their weapon.

Syntax
------

``` lua
bool reloadPedWeapon ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") who will reload their weapon.

### Returns

Returns *true* if the pedestrian was made to reload, or *false* if invalid arguments were passed or that pedestrian has a weapon which cannot be reloaded.

Note: this will fail but return true if

1) the ped is crouched and moving

2) the ped is using a weapon without clip ammo (or minigun/flamethrower/fire extinguisher)

3) the ped is using his weapon (shooting/aiming)

4) the ped moved while crouching recently

Due to these circumstances causing problems with this function

Example
-------

This example adds a 'reloadgun' console command that lets players reload their weapon.

``` lua
function reloadGun ( sourcePlayer, command )
    reloadPedWeapon ( sourcePlayer )
end
addCommandHandler ( "reloadgun", reloadGun )
```

See Also
--------
