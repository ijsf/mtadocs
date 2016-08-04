This function returns a string containing the name of the vehicle

Syntax
------

``` lua
string getVehicleName ( vehicle theVehicle )             
```

### Required Arguments

-   **theVehicle:** the [vehicle](/vehicle.md "wikilink") you want to get the name of.

### Returns

Returns a string containing the requested vehicle's name, or *false* if the vehicle passed to the function is invalid.

Example
-------

This example checks whether a player enters an AT-400 or a Shamal. If they do, it announces it to the chat specifying what vehicle was stolen.

``` lua
function planeEnter ( theVehicle, seat, jacked ) -- when someone enters a vehicle
    local id = getElementModel ( theVehicle ) -- get the model ID of the vehicle
    if id == 519 or id == 577 then -- if theVehicle is either Shamal or AT-400
        local vehicleName = getVehicleName ( theVehicle ) -- get the name of theVehicle
        outputChatBox ( "Someone has stolen a " .. vehicleName .. "!" ) -- announce that someone has stolen the plane
    end
end
-- add the event handler to the event
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), planeEnter )
```

See Also
--------

[ru:getVehicleName](/ru:getVehicleName.md "wikilink")
