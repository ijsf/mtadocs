This function gets the variant of a specified vehicle. In GTA SA some vehicles are different for example the labelling on trucks or the contents of a pick-up truck and the varying types of a motor bike. For the default GTA SA variant list see: [Vehicle variants](/Vehicle_variants.md "wikilink")

Syntax
------

``` lua
int, int getVehicleVariant ( vehicle theVehicle )
```

Required Arguments
------------------

-   **theVehicle:** A handle to the [vehicle](/vehicle.md "wikilink") that you want to get the variant of.

Returns
-------

On success:

-   **int**: An integer for the first vehicle variant see [Vehicle variants](/Vehicle_variants.md "wikilink")
-   **int**: An integer for the second vehicle variant see [Vehicle variants](/Vehicle_variants.md "wikilink")

On failure:

-   **bool**: False because the specified vehicle didn't exist

Example
-------

<section name="Client" class="client" show="true">
This example tells the person in the vehicle what their vehicle variants are using: getvehvar

``` lua
function getMyVehiclesVariant()
    local myVeh = getPedOccupiedVehicle(localPlayer) -- Get the vehicle that they're in
    if (myVeh) then
        local var1, var2 = getVehicleVariant(myVeh) -- Get the info
        outputChatBox("This vehicles variants: "..tostring(var1).." "..tostring(var2)) -- Output the info
    end
end
addCommandHandler("getvehvar", getMyVehiclesVariant)
```

</section>
Requirements
------------

See Also
--------
