Gets the name of a vehicle by its model id.

Syntax
------

``` lua
string getVehicleNameFromID ( int id )            
```

### Required Arguments

-   **id:** This is a vehicle id. See [vehicle](/vehicle.md "wikilink") to see what values will return names (true).

### Returns

Returns the name of the vehicle if the id was valid, *false* otherwise.

Example
-------

This will retrieve the name of a car so its name can be displayed when the player chooses to spawn a car by ID.

``` lua
function createvehiclecommand ( sourcePlayer, commandName, carid )
    -- This function is triggered by the text "spawnvehicle" in the console.
    -- The player must specify the parameter 'carid' to specify
    -- what car they wish to spawn.
    local x, y, z = getElementPosition ( sourcePlayer )
    -- Get the position of the player to spawn the car near this location
    local carname = getVehicleNameFromID ( tonumber(carid) )
    -- Get the name of the car the player asked for and store it in the
    -- variable 'carname'
    if carname == false then
        outputChatBox ( "That is not a valid car ID", sourcePlayer )
    else
        createVehicle ( carid, x + 5, y, z )
        -- Spawn the car at x + 5 from the player so it doesn't crush him
        outputChatBox ( "A " .. carname .. " was created!" )
    end
    -- If the entered car ID is invalid, false will be returned.
    -- Otherwise a string is returned, we create the car and announce the car name in the chatbox.
end
addCommandHandler ( "spawnvehicle", createvehiclecommand )
```

See Also
--------
