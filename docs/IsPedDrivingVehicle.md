This function checks if a specified [ped](/docs/ped.md "wikilink") or [player](/player.md "wikilink") is driving a [vehicle](/vehicle.md "wikilink").

Syntax
------

``` lua
bool, vehicle isPedDrivingVehicle ( element ped )
```

### Arguments

-   **ped**: a [player](/docs/player.md "wikilink") or [ped](/ped.md "wikilink") to check if it's driving a [vehicle](/vehicle.md "wikilink") or not.

### Returns

Returns *true* and a vehicle if the specified ped is driving a [vehicle](/docs/vehicle.md "wikilink"), *false* if it's not or a bad argument was passed.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function isPedDrivingVehicle(ped)
    assert(isElement(ped) and (getElementType(ped) == "ped" or getElementType(ped) == "player"), "Bad argument @ isPedDrivingVehicle [ped/player expected, got " .. tostring(ped) .. "]")
    local isDriving = isPedInVehicle(ped) and getVehicleOccupant(getPedOccupiedVehicle(ped)) == ped
    return isDriving, isDriving and getPedOccupiedVehicle(ped) or nil
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example adds a /amidriving command which tells the player who types it if it's driving or not.

``` lua
addCommandHandler ( "amidriving",
    function ( player )
        local driving, vehicle = isPedDrivingVehicle ( player )
        if driving then
            outputChatBox ( "* You are driving a "..getVehicleName(vehicle)..".", player, 255, 255, 0, true )
        else
            outputChatBox ( "* You are not driving.", player, 255, 0, 0, true )
        end
    end
)
```

</section>
See also
--------
