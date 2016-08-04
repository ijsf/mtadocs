This function respawns a vehicle according to its set respawn position, set by [setVehicleRespawnPosition](/docs/setvehiclerespawnposition.md "wikilink") or the position and rotation it was created on. To spawn a vehicle to a specific location just once, [spawnVehicle](/spawnVehicle.md "wikilink") can be used.

Syntax
------

``` lua
bool respawnVehicle ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle you wish to respawn

### Returns

Returns *true* if the vehicle respawned successfully, *false* if the passed argument does not exist or is not a vehicle.

Example
-------

This example makes an exploded vehicle re-spawn after 5 seconds!

``` lua
function respawnExplodedVehicle()
    setTimer(respawnVehicle, 5000, 1, source)
end
addEventHandler("onVehicleExplode", getRootElement(), respawnExplodedVehicle)
```

See Also
--------
