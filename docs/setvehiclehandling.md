This function is used to change the handling data of a vehicle.

Syntax
------

``` lua
bool setVehicleHandling ( element theVehicle, string property, var value ) 
```

Syntaxes for reset configurations:

``` lua
bool setVehicleHandling ( element theVehicle, string property, nil, false )  -- Reset one property to model handling value
bool setVehicleHandling ( element theVehicle, string property, nil, true )   -- Reset one property to GTA default value
bool setVehicleHandling ( element theVehicle, false )  -- Reset all properties to model handling value
bool setVehicleHandling ( element theVehicle, true )   -- Reset all properties to GTA default value
```

### Required Arguments

-   **theVehicle:** The vehicle you wish to set the handling of.
-   **property:** The property you wish to set the handling of the vehicle to.

-   **value:** The value of the property you wish to set the handling of the vehicle to.

### Returns

Returns *true* if the handling was set successfully, *false* otherwise. See below a list of valid propertys and their required values:

Notes
-----

for functionality reasons suspension modification is disabled on monster trucks, trains, boats and trailers.

Example
-------

This example will make Infernus handling very fast and also make it damage proof from collision (handling by Mr.unpredictable). this example will help you in creating your own vehicle Handling.

<section name="Server" class="server" show="true">
``` lua
function vhandling ( )
   for _,v in pairs(getElementsByType("vehicle")) do
      if getElementModel(v) == 411 then -------------- vehicle Id
        setVehicleHandling (v, "mass", 300.0)
        setVehicleHandling(v, "turnMass", 200)
        setVehicleHandling(v, "dragCoeff", 4.0 )
        setVehicleHandling(v, "centerOfMass", { 0.0,0.08,-0.09 } )
        setVehicleHandling(v, "percentSubmerged", 103)
        setVehicleHandling(v, "tractionMultiplier", 1.8)
        setVehicleHandling(v, "tractionLoss", 1.0)
        setVehicleHandling(v, "tractionBias", 0.48)
        setVehicleHandling(v, "numberOfGears", 5)
        setVehicleHandling(v, "maxVelocity", 300.0)
        setVehicleHandling(v, "engineAcceleration", 90.0 )
        setVehicleHandling(v, "engineInertia", 5.0)
        setVehicleHandling(v, "driveType", "rwd")
        setVehicleHandling(v, "engineType", "petrol")
        setVehicleHandling(v, "brakeDeceleration", 20.0)
        setVehicleHandling(v, "brakeBias", 0.60)
        -----abs----
        setVehicleHandling(v, "steeringLock",  35.0 )
        setVehicleHandling(v, "suspensionForceLevel", 0.85)
        setVehicleHandling(v, "suspensionDamping", 0.15 )
        setVehicleHandling(v, "suspensionHighSpeedDamping", 0.0)
        setVehicleHandling(v, "suspensionUpperLimit", 0.15 )
        setVehicleHandling(v, "suspensionLowerLimit", -0.16)
        setVehicleHandling(v, "suspensionFrontRearBias", 0.5 )
        setVehicleHandling(v, "suspensionAntiDiveMultiplier", 0.0)
        setVehicleHandling(v, "seatOffsetDistance", 0.0)
        setVehicleHandling(v, "collisionDamageMultiplier", 0.00)
        setVehicleHandling(v, "monetary",  10000)
        setVehicleHandling(v, "modelFlags", 1002000)
        setVehicleHandling(v, "handlingFlags", 1000002)
        setVehicleHandling(v, "headLight", 3)
        setVehicleHandling(v, "tailLight", 2)
        setVehicleHandling(v, "animGroup", 4)
      end
   end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), vhandling )
```

</section>
This example will add a command for players with which they can change the mass of the vehicle.

<section name="Server" class="server" show="true">
``` lua
function massChange ( me, command, mass )
    mass = tonumber ( mass ) -- Convert mass to a number
    local veh = getPedOccupiedVehicle ( me ) -- Get the player's vehicle
    
    if mass and veh then  -- If valid mass and in a vehicle
        local success = setVehicleHandling ( veh, "mass", mass ) -- Set the vehicle's mass, and check if successful
        
        if success then -- If successful
            outputChatBox ( "Your vehicle's mass has been changed to: "..mass.." kg", me, 0, 255, 0 ) -- Notify the player of success
        else -- Too bad failure is still an option
            outputChatBox ( "Setting mass failed. It's probably above or below allowed limits", me, 255, 0, 0 ) -- Notify the player of failure, and give a possible reason
        end
    elseif not veh then -- If not in a vehicle
        outputChatBox ( "You're not in a vehicle", me, 255, 0, 0 ) -- Tell the player; He / she obviously doesn't know
    elseif not mass then -- If not a valid mass
        outputChatBox ( "Syntax: /changemass [mass]", me, 255, 0, 0 ) -- Tell the player the proper syntax
    end
end
addCommandHandler ( "changemass", massChange )
```

</section>
See other vehicle functions
---------------------------
