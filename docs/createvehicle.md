This function creates a vehicle at the specified location.

Its worth noting that the position of the vehicle is the center point of the vehicle, not its base. As such, you need to ensure that the z value (vertical axis) is some height above the ground. You can find the exact height using the client side function [getElementDistanceFromCentreOfMassToBaseOfModel](/docs/getelementdistancefromcentreofmasstobaseofmodel.md "wikilink"), or you can estimate it yourself and just spawn the vehicle so it drops to the ground.

Syntax
------

``` lua
vehicle createVehicle ( int model, float x, float y, float z [, float rx, float ry, float rz, string numberplate, bool bDirection, int variant1, int variant2 ] )
```

### Required Arguments

-   **model**: The [vehicle ID](/docs/vehicle_ids.md "wikilink") of the vehicle being created.
-   **x**: A floating point number representing the X coordinate on the map.
-   **y**: A floating point number representing the Y coordinate on the map.
-   **z**: A floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **rx**: A floating point number representing the rotation about the X axis in degrees.
-   **ry**: A floating point number representing the rotation about the Y axis in degrees.
-   **rz**: A floating point number representing the rotation about the Z axis in degrees.
-   **numberplate**: A string that will go on the number plate of the vehicle (max 8 characters).
-   **bDirection** *(serverside only)*: Placeholder [boolean](/docs/boolean.md "wikilink") which provides backward compatibility with some scripts. It never had any effect, but it is read by the code. It is recommended to ignore this argument, passing *false* or the *variant1* argument in its place.

### Returns

Returns the [vehicle](/docs/vehicle.md "wikilink") element that was created. Returns *false* if the arguments are incorrect, or if the vehicle limit of 65535 is exceeded.

Using trains
------------

Trains are created using the createVehicle function. They are placed at the nearest point of the GTASA train pathing (they usually are railroad tracks) from their spawning point.

Example
-------

<section name="Example 1: Server" class="server" show="true">
This example creates a vehicle five units to the right of a player when they type *createvehicle* and its name in the console:

``` lua
local distance = 5 --units

-- define our handler (we'll take a variable number of parameters where the name goes, because there are vehicle names with more than one word)
function consoleCreateVehicle ( sourcePlayer, commandName, ... )
   -- if a player triggered it, not the admin,
   if ( sourcePlayer ) then
      -- calculate the position of the vehicle based on the player's position and rotation:
      local x, y, z = getElementPosition ( sourcePlayer ) -- get the player's position
      local rotZ = getPedRotation ( sourcePlayer ) -- get the player's rotation around the Z axis in degrees
      x = x + ( ( math.cos ( math.rad ( rotZ ) ) ) * distance ) -- calculate the X position of the vehicle
      y = y + ( ( math.sin ( math.rad ( rotZ ) ) ) * distance ) -- calculate the Y position of the vehicle

      -- get the complete vehicle name by joining all passed parameters using Lua function table.concat
      local vehicleName = table.concat({...}, " ")
      -- get the vehicle's model ID from the name
      local vehicleID = getVehicleModelFromName ( vehicleName )
      -- if vehicle ID is valid,
      if vehicleID then
            -- create the vehicle using the information gathered above:
            local newVehicle = createVehicle ( vehicleID, x, y, z, 0, 0, rotZ )
            -- if vehicle creation failed, give the player a message
            if not newVehicle then
               outputConsole ( "Failed to create vehicle.", sourcePlayer )
            end
      end
   end
end

-- Attach the 'consoleCreateVehicle' function to the "createvehicle" command
addCommandHandler ( "createvehicle", consoleCreateVehicle )
```

</section>
<section name="Example 2: Server" class="server" show="false">
This script spawns a Rhino on top of one lucky individual.

``` lua
function scriptCreateTank ( player, command )
      local luckyBugger = getRandomPlayer() -- get a random player
      local x, y, z = getElementPosition ( luckyBugger ) -- retrive the player's position
      createVehicle ( 432, x, y, z + 10 ) -- create the tank 10 units above them
      outputChatBox ( "You got Tank'd!", luckyBugger )
end
--Attach the 'scriptCreateTank' function to the "tank" command
addCommandHandler ( "tank", scriptCreateTank )
```

</section>
<section name="Example 3: Server" class="server" show="false">
This example adds a */spveh* command to spawn a car model in the provided coordinates. If any car created by this command gets blown up, it will respawn where it was created.

``` lua
-- Do not allow the following IDs to be spawned
local forbiddenCars = { [435] = true, [441] = true, [449] = true, [450] = true, [464] = true, [465] = true, [501] = true,
                        [537] = true, [538] = true, [564] = true, [569] = true, [570] = true, [584] = true, [590] = true,
                        [591] = true, [594] = true, [606] = true, [607] = true, [608] = true, [610] = true, [611] = true }

local cmdVehRoot = createElement("commandVehicles") -- Dummy element containing the cars that this command has created
addCommandHandler("spveh",
    function(player, cmd, modelID, x, y, z, platetext)
        -- Check whether arguments are correct
        local modelID, x, y, z = tonumber(modelID), tonumber(x), tonumber(y), tonumber(z)
        if modelID and x and y and z then
            -- Do not continue if we shouldn't
            if forbiddenCars[modelID] then
                outputChatBox("The car model you provided is not allowed.", player, 255, 0, 0)
                return
            end
            local platetext = type(platetext) == "string" and platetext or "PRIVATE"
            -- Create the actual vehicle and set it as a children of our dummy element
            setElementParent(createVehicle(modelID, x, y, z, 0, 0, 0, platetext), cmdVehRoot)
            -- Inform the player about what we did
            outputChatBox("You have created a " .. getVehicleNameFromModel(modelID) .. " (model ID: " .. modelID .. ") at " .. table.concat({ x, y, z }, ", ") .. " with numberplate " .. platetext .. " successfully.", player, 0, 255, 0)
        else
            outputChatBox("Syntax: /" .. cmd .. " (modelID) (x) (y) (z) [numberplate]", player, 255, 255, 255)
        end
    end
)

-- If a vehicle that has been created using the command blows up, respawn it where it was created
addEventHandler("onVehicleExplode", cmdVehRoot,
    function()
        respawnVehicle(source)
    end
)
```

</section>
<section name="Example 3: Client" class="client" show="true">
This script spawns a Rhino on top of the local player.

``` lua
function scriptCreateTank ( commandName )
      local luckyBugger = getLocalPlayer() -- get the local player
      local x, y, z = getElementPosition ( luckyBugger ) -- retrive the player's position
      createVehicle ( 432, x, y, z + 10 ) -- create the tank 10 units above them
      outputChatBox ( "You got Tank'd!", 255, 0, 0)
end
--Attach the 'scriptCreateTank' function to the "tank" command
addCommandHandler ( "tank", scriptCreateTank )
```

</section>
See Also
--------

[de:createVehicle](/docs/de:createvehicle.md "wikilink") [pl:createVehicle](/docs/pl:createvehicle.md "wikilink") [RU:CreateVehicle](/docs/ru:createvehicle.md "wikilink")
