This function is used to warp or force a ped into a vehicle. There are no animations involved when this happens.

**Available client side from 1.3.1** (It will only work with client side vehicles and peds)

<div style="background: #FF7070; border: 3px solid #FF0000;">
**Attention:** If you used [setElementPosition](/setElementPosition.md "wikilink") to spawn the [ped](/ped.md "wikilink")/[player](/player.md "wikilink"), this function will not work and returns **false**.

</div>
Syntax
------

``` lua
bool warpPedIntoVehicle ( ped thePed, vehicle theVehicle, [ int seat=0 ] )          
```

### Required Arguments

-   **thePed:** The ped which you wish to force inside the vehicle
-   **theVehicle:** The vehicle you wish to force the ped into

### Optional Arguments

-   **seat:** An integer representing the seat ID. *0* represents the driver, any higher represent passenger seats.

### Returns

Returns *true* if the operation is successful, *false* otherwise.

Example
-------

This example creates a vehicle and warps a ped inside immediately.

``` lua
function setupForRace ( )
    local RacerPed = createPed ( 252, 0, 0, 3 )
    local RaceVehicle = createVehicle ( 411, 4, 0, 3 )            -- create a vehicle.
    warpPedIntoVehicle ( RacerPed, RaceVehicle )                  -- warp the ped straight into the vehicle
end
addCommandHandler ( "startrace", setupForRace )                   -- add a command to start race
```

Issues
------

See Also
--------

[ru:warpPedIntoVehicle](/ru:warpPedIntoVehicle.md "wikilink")
