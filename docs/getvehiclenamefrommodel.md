Gets the name of a vehicle by its model ID.

Syntax
------

``` lua
string getVehicleNameFromModel ( int model )            
```

### Required Arguments

-   **model:** This is the vehicle model ID. See [vehicle IDs](/docs/vehicle_ids.md "wikilink") to see what values will return names.

### Returns

Returns the name of the vehicle if the model ID was valid, empty string otherwise[1].

Example
-------

This will retrieve the name of a car so its name can be displayed when the player chooses to spawn a car by model ID.

``` lua
function createVehicleCommand ( thePlayer, commandName, carModel )
    -- This function is triggered by the text "spawnvehicle" in the console.
    -- The player must specify the parameter 'carModel' to specify
    -- what car they wish to spawn.
    local x, y, z = getElementPosition ( thePlayer )
    -- Get the position of the player to spawn the car near this location
    local carName = getVehicleNameFromModel ( tonumber ( carModel ) )
    -- Get the name of the car the player asked for and store it in the
    -- variable 'carName'
    if not carname then
        outputChatBox ( "That is not a valid car model ID", thePlayer )
    else
        createVehicle ( tonumber ( carModel ), x + 5, y, z )
        -- Spawn the car at x + 5 from the player so it doesn't crush him
        outputChatBox ( "A " .. carName .. " was created!" )
    end
    -- If the entered car model ID is invalid, false will be returned.
    -- Otherwise a string is returned, we create the car and announce the car name in the chatbox.
end
addCommandHandler ( "spawnvehicle", createVehicleCommand )
```

References
----------

<references />
See Also
--------

[1] <https://bugs.multitheftauto.com/view.php?id=8523>
