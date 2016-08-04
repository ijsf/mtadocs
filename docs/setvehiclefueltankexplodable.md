This function changes the 'explodable state' of a vehicle's fuel tank, which toggles the ability to blow the vehicle up by shooting the tank. This function will have no effect on vehicles with tanks that cannot be shot in single player.

Syntax
------

``` lua
bool setVehicleFuelTankExplodable ( vehicle theVehicle, bool explodable )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/docs/vehicle.md "wikilink") you wish to change the fuel tank explodable state of.
-   **explodable**: A boolean value representing whether or not the fuel tank will be explodable.

### Returns

Returns *true* if the vehicle's fuel tank explodable state was successfully changed, *false* otherwise.

Example
-------

<section name="Serverside example" class="server" show="true">
This example will make vehicles' fuel tanks explodable for 10 seconds after they're entered.

``` lua
-- create a table to keep track of vulnerable vehicles
-- so we don't set the state-reset timer twice when reentering a vulnerable vehicle
local isVulnerable = {}

-- this function makes a vehicle vulnerable and sets a timer to unset it in 10 seconds
function setVehicleVulnerable ( theVehicle, enteredSeat )
    -- we'll ignore vehicles that are already vulnerable.
    if not isVulnerable[theVehicle] then
        -- if they're getting into the driver seat
        if enteredSeat == 0 then
            -- make the fuel tank explodable
            setVehicleFuelTankExplodable ( theVehicle, true )
            -- flag this vehicle as vulnerable
            isVulnerable[theVehicle] = true
            -- make it non vulnerable in 10 seconds
            setTimer ( unsetVehicleVulnerable, 10000, 1, theVehicle )
        end
    end
end

-- this function makes a vehicle not vulnerable
function unsetVehicleVulnerable ( theVehicle )
    -- make the fuel tank unexplodable
    setVehicleFuelTankExplodable ( theVehicle, false )
    -- remove the vulnerable flag
    isVulnerable[theVehicle] = nil
end

-- add the 'makeVehicleVulnerable' function as a handler for "onPlayerVehicleEnter"
addEventHandler ( "onPlayerVehicleEnter", getRootElement ( ), setVehicleVulnerable )
```

</section>
See Also
--------
