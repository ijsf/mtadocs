This function is used to retrieve the text on the number plate of a specified vehicle.

Syntax
------

``` lua
string getVehiclePlateText ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** the [vehicle](/vehicle.md "wikilink") that you wish to retrieve the plate text from.

### Returns

Returns a *string* that corresponds to the plate on the text, *false* if a bad argument was passed or if it is not a vehicle. Every vehicle (including planes, boats, etc.) has a numberplate, even if it's not visible.

Example
-------

<section name="Client" class="client" show="true">
This example outputs the text on the license plate of the vehicle the player is driving to the chatbox.

``` lua
function outputLicensePlate ( command )
    if isPedInVehicle(localPlayer) then --let's check if they're in a vehicle
         -- if they are in a vehicle
         local vehicle = getPedOccupiedVehicle ( localPlayer ) --let's get the vehicle
         local plateText = getVehiclePlateText ( vehicle ) --get the license plate text
         if plateText then -- if there was a license plate,
             outputChatBox ( "Your license plate is: " .. plateText )-- output it to the chatbox
         else
             outputChatBox ( "Your vehicle has no license plate." )
         end
    else
         outputChatBox ( "You're not in a vehicle." )
    end
end
-- add our function as a handler to the "plate" command
addCommandHandler( "plate", outputLicensePlate )
```

</section>
See Also
--------
