This functions makes a vehicle damage proof, so it won't take damage from bullets, hits, explosions or fire. A damage proof's vehicle health can still be changed via script.

Syntax
------

``` lua
bool setVehicleDamageProof ( vehicle theVehicle, bool damageProof )
```

### Required Arguments

-   **theVehicle:** The [vehicle](/vehicle.md "wikilink") you wish to make damage proof.
-   **damageProof:** *true* is damage proof, *false* is damageable.

### Returns

Returns *true* if the vehicle was set damage proof succesfully, *false* if the arguments are invalid or it failed.

Example
-------

This example spawns a vehicle and sets it damage proof immediately.

``` lua
newvehicle = createVehicle(602, 0, 0, 6)
setVehicleDamageProof(newvehicle, true)
```

See Also
--------
