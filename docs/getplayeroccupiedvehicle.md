This function gets the [vehicle](/docs/vehicle.md "wikilink") that the player is currently in, if any.

Syntax
------

``` lua
vehicle getPlayerOccupiedVehicle ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") whose vehicle you're looking up.

### Returns

Returns the vehicle that the specified player is in, or *false* if the player is not in a vehicle or is an invalid player.

Example
-------

When a player enters the 'vehiclename' command and is currently in a vehicle, this example outputs the name of the vehicle.

<section name="Server and client" class="both" show="true">
``` lua
function showVehicleName ( thePlayer )
    local theVehicle = getPlayerOccupiedVehicle ( thePlayer )
    if ( theVehicle ) then
        local vehicleName = getVehicleName ( theVehicle )
        outputChatBox ( "Vehicle name: " .. vehicleName, thePlayer )
    end
end
addCommandHandler ( "vehiclename", showVehicleName )
```

</section>
See Also
--------
