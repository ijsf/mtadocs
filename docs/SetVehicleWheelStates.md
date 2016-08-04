This function sets the state of wheels on the vehicle.

Internally, no vehicles have more than 4 wheels. If they appear to, they will be duplicating other wheels.

Syntax
------

``` lua
)
```

Required Arguments
------------------

-   **theVehicle:** A handle to the [vehicle](/vehicle.md "wikilink") that you wish to change the wheel states of.
-   **frontLeft:** A whole number representing the wheel state (-1 for no change)

Optional Arguments
------------------

-   **rearLeft:** A whole number representing the wheel state (-1 for no change)
-   **frontRight:** A whole number representing the wheel state (-1 for no change)
-   **rearRight:** A whole number representing the wheel state (-1 for no change)

Wheel-State values
------------------

-   **0:** Inflated
-   **1:** Flat
-   **2:** Fallen off
-   **3:** Collisionless

Returns
-------

Returns a boolean value *true* or *false* that tells you if it was successful or not.

Example
-------

<section name="Server" class="server" show="true">
This example displays the states of the vehicle's wheels and changes their states if any arguments were passed.

``` lua
function scriptWheelStates ( thePlayer, command, newFLeft, newRLeft, newFRight, newRRight )
    local theVehicle = getPedOccupiedVehicle ( thePlayer )
    if ( theVehicle ) then      -- check if the player is in a car
        if ( newFLeft ) then    -- if there's at least one argument passed, we change the wheel states
            if not setVehicleWheelStates ( theVehicle, newFLeft, newRLeft, newFRight, newRRight ) then
                outputChatBox ( "Bad arguments." )
            end
        end
        local states = { [0]="inflated", [1]="flat", [2]="fallen off" }    -- we store the states in a table
        local frontLeft, rearLeft, frontRight, rearRight = getVehicleWheelStates ( theVehicle )
        outputChatBox ( "Your vehicle's wheel states:", thePlayer )        -- output them in the chatbox
        outputChatBox ( "Front-Left: " .. states [ frontLeft ] .. ", Front-Right: " .. states [ frontRight ] ..
           ", Rear-Left: " .. states [ rearLeft ] .. ", Rear-Right: " .. states [ rearRight ], thePlayer )
    else
        outputChatBox ( "You have to be in a vehicle to use this command.", thePlayer )
    end
end
addCommandHandler ( "wheelstates", scriptWheelStates )
```

</section>
<section name="Client" class="client" >
This example displays the states of the vehicle's wheels and changes their states if any arguments were passed.

``` lua
function scriptWheelStates (command, newFLeft, newRLeft, newFRight, newRRight )
    local theVehicle = getPedOccupiedVehicle ( localPlayer )
    if ( theVehicle ) then      -- check if the player is in a car
        if ( newFLeft ) then    -- if there's at least one argument passed, we change the wheel states
            if not setVehicleWheelStates ( theVehicle, newFLeft, newRLeft, newFRight, newRRight ) then
                outputChatBox ( "Bad arguments." )
            end
        end
        local states = { [0]="inflated", [1]="flat", [2]="fallen off" }    -- we store the states in a table
        local frontLeft, rearLeft, frontRight, rearRight = getVehicleWheelStates ( theVehicle )
        outputChatBox ( "Your vehicle's wheel states:", localPlayer )        -- output them in the chatbox
        outputChatBox ( "Front-Left: " .. states [ frontLeft ] .. ", Front-Right: " .. states [ frontRight ] ..
           ", Rear-Left: " .. states [ rearLeft ] .. ", Rear-Right: " .. states [ rearRight ], localPlayer )
    else
        outputChatBox ( "You have to be in a vehicle to use this command.", localPlayer )
    end
end
addCommandHandler ( "wheelstates", scriptWheelStates )
```

</section>
See Also
--------
