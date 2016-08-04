Syntax
------

``` lua
string getVehicleType ( vehicle theVehicle )
```

**OR**

``` lua
string getVehicleType ( int modelId )
```

### Required Arguments

-   **vehicle:** The vehicle element to get the type of.

**OR**

-   **modelID:** A vehicle model ID

### Returns

Returns a *string* with vehicle type or *false* if an invalid modelID has been supplied, or an empty string if the vehicle is blocked internally (some trailers).

Possible strings returned:

Example
-------

**Example 1:** In this example when a player enters an airplane, it displays a message welcoming the player onboard.

``` lua
function enterPlane(theVehicle, seat, jacked)
    if (getVehicleType(theVehicle) == "Plane") then
        outputChatBox("Welcome onboard!", source)
    end
end

addEventHandler("onPlayerVehicleEnter", getRootElement(), enterPlane)
```

**Example 2:** In this example player gets message what type of vehicle he just entered.

``` lua
function enteredVehicleType(theVehicle, seat, jacked)
    outputChatBox("You entered ".. getVehicleType(theVehicle) ..".", source)
end

addEventHandler("onPlayerVehicleEnter", getRootElement(), enteredVehicleType)
```

See Also
--------
