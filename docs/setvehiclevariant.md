This function sets the variant of a specified vehicle. In GTA SA some vehicles are different for example the labelling on trucks or the contents of a pick-up truck and the varying types of a motor bike. For the default GTA SA variant list see: [Vehicle variants](/docs/Vehicle_variants.md "wikilink")

` `
` `
` `

Syntax
------

``` lua
 )
```

Required Arguments
------------------

-   **theVehicle:** A handle to the [vehicle](/docs/vehicle.md "wikilink") that you want to get the variant of.

Optional Arguments
------------------

Both arguments need to be supplied, otherwise random variants will be picked.

-   **variant1**: An integer for the first variant see [Vehicle variants](/docs/Vehicle_variants.md "wikilink")
-   **variant2**: An integer for the second variant see [Vehicle variants](/docs/Vehicle_variants.md "wikilink")

Returns
-------

On success:

-   **bool**: Returns true as the vehicle variants were successfully set.

On failure:

-   **bool**: False because the specified vehicle didn't exist or specified variants were invalid.

Example
-------

This example lets the vehicle driver set their vehicle variant with setvehvar

``` lua
function setMyVehiclesVariant(theUser, command, var1, var2)
    local var1, var2 = tonumber(var1), tonumber(var2) -- If anything was passed make sure its number or nil
    local myVeh = getPedOccupiedVehicle(theUser) -- Get the vehicle that they're in
    if (myVeh and getVehicleController(myVeh) == theUser) then -- Make sure they're in control
        local wasSet = setVehicleVariant(myVeh, var1, var2) -- Set what they wanted
        if (wasSet) then
            outputChatBox("Vehicle variant successfully set!", theUser, 0, 255, 0)
        else
            outputChatBox("Vehicle variant unsuccessfully set.", theUser, 255, 255, 0)
        end
    end
end
addCommandHandler("setvehvar", setMyVehiclesVariant) -- Add the command
```

Requirements
------------

See Also
--------
