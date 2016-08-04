This function removes a player from a vehicle immediately. This works for drivers and passengers. Note that this removes the player from the vehicle and puts him in the exact position where the command was initiated.

Syntax
------

``` lua
bool removePlayerFromVehicle ( player thePlayer )           
```

### Required Arguments

-   **thePlayer:** The player you wish to remove from a vehicle

### Returns

Returns *true* if the operation was successful, *false* otherwise.

Example
-------

This example forces a player out of a police vehicle if he is not a policeman.

``` lua
local policevehicles = { [596]=true, [597]=true, [598]=true, [599]=true }  -- make a table of police vehicle IDs
local policeskins = { [283]=true, [284]=true, [285]=true, [286]=true }     -- make a table of police skin IDs
function enterVehicle ( theVehicle, seat, jacked )                         -- when a player enters a vehicle
    local skinID = getPlayerSkin ( source )                                -- get his skin ID
    local vehID = getVehicleID ( theVehicle )
    if policevehicles[vehID] and not policeskins[skinID] then              -- if the vehicle is one of 4 police cars, and the skin is not a police skin
        removePlayerFromVehicle ( source )                                 -- force the player out of the vehicle
        outputChatBox ( "Only policemen can enter police cars!", source )  -- and tell the player why
    end
end
addEventHandler ( "onPlayerEnterVehicle", getRootElement(), enterVehicle ) -- add an event for onPlayerEnterVehicle
```

See Also
--------
