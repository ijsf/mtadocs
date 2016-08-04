This function returns a table of the original vehicle handling. Use [getVehicleHandling](/docs/getVehicleHandling.md "wikilink") if you wish to get the current handling of a vehicle, or [getModelHandling](/getModelHandling.md "wikilink") for a specific vehicle model.

Syntax
------

``` lua
table getOriginalHandling ( int modelID ) 
```

### Required Arguments

-   **modelID:** The vehicle ID you wish to get the original handling from.

### Returns

Returns a *table* containing all the handling data, *false* otherwise. Here a list of valid table properties and what they return:

Example
-------

<section name="Server & Client" class="both" show="true">
This example creates a new function called getVehicleOriginalProperty, which simulates the previous syntax of this function.

``` lua
function getVehicleOriginalProperty( element, property )
    if isElement ( element ) and getElementType ( element ) == "vehicle" and type ( property ) == "string" then -- Make sure there's a valid vehicle and a property string
        local modelID = getElementModel ( element )
        local handlingTable = getOriginalHandling ( modelID ) -- Get the handling as table and save as handlingTable
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
