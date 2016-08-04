This function retrieves the ID of a vehicle as an integer value from its name.

Syntax
------

``` lua
int getVehicleIDFromName ( string name )             
```

### Required Arguments

-   **name:** A [string](/string.md "wikilink") containing the name of the vehicle.

### Returns

Returns an [int](/int.md "wikilink") if the name exists, *false* otherwise. If you use this function on vehicles with shared names, such as “police”, it will return the earliest occurrence of that vehicle's ID.

Example
-------

This will allow the player to create a vehicle by name and it's ID will be displayed in the chatbox when the vehicle is spawned.

``` lua
function createvehiclecommand ( sourcePlayer, commandName, carname )
    -- This function is triggered by the text "spawnvehicle" in the console.
    -- The player must specify the added parameter 'carname' to specify
    -- what car they wish to spawn.
    local carid = getVehicleIDFromName ( carname )
    -- Get the ID of the car the player asked for and store it to the
    -- variable 'carid'
    local x, y, z = getElementPosition ( sourcePlayer )
    -- Get the position of the player to spawn the car near this location
    if carid == false then
        outputChatBox ( "That is not a valid car name" )
    else
        createVehicle ( carid, x + 5, y, z )
        -- Spawn the car using its ID. Spawn it at x + 5 from the player so it doesn't crush him
        outputChatBox ( "A vehicle with an ID of " .. carid .. " was created!" )
    end
    -- If the entered car name returns no car ID, the string will be empty and false will be returned.
    -- If the string does have any value, we create the car and announce the car ID in the chatbox,
    -- because a car did exist under the given car name.
end
addCommandHandler ( "spawnvehicle", createvehiclecommand )
```

See Also
--------
