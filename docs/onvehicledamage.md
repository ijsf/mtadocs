This event is triggered when a vehicle is damaged.

Parameters
----------

``` lua
float loss
```

-   **loss**: A float representing the amount of health the vehicle lost.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [vehicle](/vehicle.md "wikilink") that got damaged.

Example
-------

This example displays a message with the amount of health lost when a vehicle gets damaged.

``` lua
function displayVehicleLoss(loss)
    local thePlayer = getVehicleOccupant(source)
    if(thePlayer) then -- Check there is a player in the vehicle
        outputChatBox("Your vehicle just lost " .. tonumber(loss) .. " health.", thePlayer) -- Display the message
    end
end

addEventHandler("onVehicleDamage", getRootElement(), displayVehicleLoss)
```
