This function will check if a train or tram is derailable.

Syntax
------

``` lua
bool isTrainDerailable ( vehicle vehicleToCheck )              
```

### Required Arguments

-   **vehicleToCheck:** The vehicle you wish to check.

### Returns

Returns *true* if the train is derailable, *false* otherwise.

Example
-------

This example warns the player if their train can be derailed.

<section name="Client" class="client" show="true">
``` lua
local function playerVehicleEnter()
    local localVehicle = getPedOccupiedVehicle(localPlayer)
    if not isElement(localVehicle) then return end -- In case getPedOccupiedVehicle() does not return a valid vehicle, for whatever reason
    
    if getVehicleType(localVehicle) == "Train" then
        if isTrainDerailable(localVehicle) then
            outputChatBox("* Warning: this train could derail!", 255, 0, 0)
        end
    end
end
addEventHandler("onClientPlayerVehicleEnter", localPlayer, playerVehicleEnter)
```

</section>
See Also
--------
