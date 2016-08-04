Syntax
------

``` lua
table getVehicleSirens ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** The vehicle to get siren information of.

### Returns

If the vehicle is invalid, it returns *false*. Otherwise, returns a *table* with sub tables containing the properties of each siren point in the following manner:

``` lua
[float]   SirenData[sirenPoint].x
[float]   SirenData[sirenPoint].y
[float]   SirenData[sirenPoint].z
[int]     SirenData[sirenPoint].Red
[int]     SirenData[sirenPoint].Green
[int]     SirenData[sirenPoint].Blue
[int]     SirenData[sirenPoint].Alpha
[int]     SirenData[sirenPoint].Min_Alpha
```

Example
-------

<section name="Server" class="server" show="true">
This example returns the siren properties when the player presses Z.

``` lua
addEventHandler("onVehicleEnter", root, function(player, seat)
   if seat == 0 then -- If a player starts driving a vehicle...
      -- ... customize the vehicle sirens and bind a key to ouput info about them to the driver
      addVehicleSirens(source, 1, 1)
      setVehicleSirens(source, 1, 0, 0, 0, 100, 0, 100, 255, 122)
      bindKey(player, "z", "up", outputSirenInfoToPlayer, source)
   end
end)

function outputSirenInfoToPlayer(player, _, _, vehicle)
   -- Get vehicle's siren data and output it to the player in the chatbox
   local sirenData = getVehicleSirens(vehicle)
   outputChatBox("These are the properties of your vehicle's siren:", player, 0, 255, 0)
   outputChatBox("RGB siren colour: " .. sirenData[1].Red .. ", " .. sirenData[1].Green .. ", " .. sirenData[1].Blue .. ".", player)
   outputChatBox("Maximum alpha (during bad visibility conditions): " .. sirenData[1].Alpha .. ", minimum alpha (during good visibility conditions): " .. sirenData[1].Min_Alpha .. ".", player)
   outputChatBox("Siren light position: " .. sirenData[1].x .. ", " .. sirenData[1].y .. ", " .. sirenData[1].z .. ".", player)
end

addEventHandler("onVehicleStartExit", root, function(player, seat)
   if seat == 0 then -- If a player stops driving a vehicle...
      -- ... remove vehicle's sirens and unbind the key
      removeVehicleSirens(source)
      unbindKey(player, "z", "up", outputSirenInfoToPlayer)
   end
end)
```

</section>
Requirements
------------

See Also
--------
