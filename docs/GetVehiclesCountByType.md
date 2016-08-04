This function returns the amount of vehicles by the given type (see [GetVehicleType](/docs/GetVehicleType.md "wikilink")) as an integer value.

### Authors

-   **Uc.Setlings**: Original code and idea
-   **Necktrox**: Code quality and performance edits

Syntax
------

``` lua
int getVehiclesCountByType ( string vehicleType )
```

### Required arguments

-   **vehicleType**: The vehicle type string (see list below).

### Vehicle type list

### Return

Returns an *integer* with the count of the vehicles with the type (returns *0* if the type is not supported), otherwise returns *nil*.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getVehiclesCountByType(vehicleType)
    assert(type(vehicleType) == "string", "expected string at argument 1, got ".. type(vehicleType))

    local getVehicleType = getVehicleType -- Localize
    local vehicleList = getElementsByType("vehicle")
    local vehicleCount = #vehicleList
    local typeCount = 0

    for index = 1, vehicleCount do
        if getVehicleType(vehicleList[index]) == vehicleType then
            typeCount = typeCount + 1
        end
    end

    return typeCount
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example writes the amount of each vehicle type into the server log every minute.

``` lua
local types = {
    "Automobile",
    "Plane",
    "Bike",
    "Helicopter",
    "Boat",
    "Train",
    "Trailer",
    "BMX",
    "Monster Truck",
    "Quad"
}

function outputVehicleCountToServerLog()
    for index, typeName in ipairs(types) do
        local count = getVehiclesCountByType(typeName)
        outputServerLog(("Amount of '%s' vehicles: %d"):format(typeName, count))
    end
end

addEventHandler("onResourceStart", resourceRoot,
    function ()
        outputVehicleCountToServerLog()
        setTimer(outputVehicleCountToServerLog, 60e3, 0)
    end,
false)
```

</section>
Example 2
---------

<section name="Server" class="server" show="true">
This example writes the amount of vehicles on the specified type, and sends the results to the server console.

``` lua
function getVehiclesCountByType(vehicleType)
    assert(type(vehicleType) == "string", "expected string at argument 1, got ".. type(vehicleType))
 
    local getVehicleType = getVehicleType -- Localize
    local vehicleList = getElementsByType("vehicle")
    local vehicleCount = #vehicleList
    local typeCount = 0
 
    for index = 1, vehicleCount do
        if getVehicleType(vehicleList[index]) == vehicleType then
            typeCount = typeCount + 1
        end
    end
 
    return typeCount
end

function IfElse(condition, resultTrue, resultFalse)
      if (not condition) then
      return resultFalse
else
      return resultTrue
   end
end

local stringType = { ["Automobile"] = true,
                     ["Plane"] = true,
                     ["Bike"] = true,
                     ["Helicopter"] = true,
                     ["Boat"] = true,
                     ["Train"] = true,
                     ["Trailer"] = true,
                     ["BMX"] = true,
                     ["Monster Truck"] = true,
                     ["Quad"] = true
                   }

addCommandHandler("amountvehicle", function(aElement, commandName, typevehicle)
                   if (getElementType(aElement) == "console") then
                   if (type(typevehicle) ~= "string") or (tostring(typevehicle) == nil) or (tostring(typevehicle) == "") or (string.len(typevehicle) < 3) then
                      outputServerLog("Correct syntax: amountvehicle <Type Vehicle>")
                return
                   end
         if stringType[tostring(typevehicle)] then
         outputServerLog(("[Vehicles By Type - '%s'] - "..IfElse(getVehiclesCountByType(typevehicle) < 1, " Not found!", "Found '%s'")):format(typevehicle, getVehiclesCountByType(typevehicle)))
else
         outputServerLog("#ERROR! The entered this syntax - '"..tostring(typevehicle).."' isn't correct")
      end
   end
end)
```

</section>
See also
--------
