This function detaches an already attached trailer from a vehicle.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/docs/vehicle.md "wikilink") you wish to detach a trailer from.

### Optional Arguments

-   **theTrailer**: The trailer you wish to be detached.

Note: If 'theTrailer' is specified, it will only detach if this matches. If it is not specified, any trailer attached to 'theVehicle' will be detached.

Returns
-------

Returns 'true' if the vehicle's were successfully detached, 'false' otherwise.

Example
-------

**Example 1:** A command for players to detach a trailer attached to their vehicle:

``` lua
-- the handler function for the "unhook" console command
function unhookTrailer(playerSource, commandName)
   -- check if a player triggered this command and that they are in a vehicle
   if (playerSource and isPedInVehicle(playerSource)) then
      local theVehicle = getPedOccupiedVehicle(playerSource) -- get the vehicle the player is in
      local success = detachTrailerFromVehicle(theVehicle) -- attempt to detach a trailer from this vehicle
      -- report whether the operation waa a success
      if (success) then
         outputConsole("Trailer detached!", playerSource)
      else
         outputConsole("Failed to detach trailer.", playerSource)
      end
   end
end

-- make the function above handle the "unhook" command
addCommandHandler("unhook", unhookTrailer)
```

**Example 2:** This example attaches a trailer to a truck, and detaches it if the trailer is damaged:

``` lua
function onTruckDamage ( loss )
   if ( loss > 50 ) then --if the health loss was more than 50
      detachTrailerFromVehicle ( source ) --detach the truck from the trailer
      -- remove the event handler so that this function is no longer called when the trailer is damaged
      removeEventHandler ( "onVehicleDamage", source, onTrailerDamage )
   end
end

function createVehiclesAndAttachThem ()
   local theTruck = createVehicle ( 515, 500, 500, 40 ) -- create a trailer-tower (roadtrain)
   local theTrailer = createVehicle ( 435, 500, 505, 40 ) -- create a trailer
   attachTrailerToVehicle ( theTruck, theTrailer ) -- attach them
   -- add an event handler for when the trailer is damaged
   addEventHandler ( "onVehicleDamage", theTruck, onTruckDamage )
end
```

See Also
--------
