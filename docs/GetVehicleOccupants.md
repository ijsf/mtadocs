This function gets all players sitting in the specified vehicle.

Syntax
------

``` lua
table getVehicleOccupants ( vehicle theVehicle )            
```

### Required Arguments

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") of which you wish to retrieve the occupants.

### Returns

Returns a [table](/docs/table.md "wikilink") with seat ID as an index and the occupant as an element like this: table\[seat\] = occupant

Returns *false* if an invalid vehicle was passed or if the vehicle has no seats (like a trailer)

<div style='font-weight: bold;background:blue;color:white;padding:2px; padding-left:8px;'>
COUNTING PLAYERS IN A VEHICLE

</div>
<div style='border: 2px solid blue;padding: 5px;'>
Don't use an ipairs loop with the table returned by this function. It will skip the driver, as ipairs starts at 1 and the driver seat is ID 0. And if there's an empty seat, ipairs will stop looping. You should use a pairs loop instead.

``` lua
local counter = 0

for seat, player in pairs(getVehicleOccupants(pseudoVehicle)) do
    counter = counter + 1
end

outputDebugString("Players in your vehicle: ".. counter)
```

</div>
Example
-------

This example prints all vehicle occupants into the F8 console if "/occupants" is typed:

``` lua
function outputOccupants(player)
    -- Make sure they're in a vehicle
    if (not isPedInVehicle(player)) then
        outputConsole("You're not in a vehicle.", player)
        return false
    end
    outputConsole("------------------------------------", player) -- Print a separator for easier reading
    local vehicle = getPedOccupiedVehicle(player)
    local occupants = getVehicleOccupants(vehicle) or {} -- In case it returned false, loop an empty table.
    for seat, occupant in pairs(occupants) do -- Loop through the array
        if (occupant and getElementType(occupant) == "player") then -- Make sure the occupant is a player
            outputConsole("Seat " .. seat .. ": " .. getPlayerName(occupant), player) -- Print who's in the seat
        end
    end
    outputConsole("------------------------------------", player) -- Print another separator
end
addCommandHandler("occupants", outputOccupants) -- Add a command "/occupants" which triggers outputOccupants
```

See Also
--------
