This function returns a table of the current vehicle handling data.

Syntax
------

``` lua
table getVehicleHandling ( element theVehicle )
```

### Required Arguments

-   **theVehicle:** the vehicle you wish to get the handling data of.

### Returns

Returns a *table* containing all the handling data, *false* otherwise. Here's a list of valid table properties and what they return:

Example
-------

<section name="Server & Client" class="both" show="true">
This example creates a new function called getVehicleHandlingProperty, which simulates the previous syntax of this function.

``` lua
function getVehicleHandlingProperty ( element, property )
    if isElement ( element ) and getElementType ( element ) == "vehicle" and type ( property ) == "string" then -- Make sure there's a valid vehicle and a property string
        local handlingTable = getVehicleHandling ( element ) -- Get the handling as table and save as handlingTable
        local value = handlingTable[property] -- Get the value from the table
        
        if value then -- If there's a value (valid property)
            return value -- Return it
        end
    end
    
    return false -- Not an element, not a vehicle or no valid property string. Return failure
end
```

</section>
See other vehicle functions
---------------------------
