<lowercasetitle/>

This function checks whether a vehicle is empty.

Syntax
------

``` lua
bool isVehicleEmpty ( vehicle theVehicle )
```

-   **theVehicle**: The vehicle that you want to check.

Code
----

<section name="Serverside/Clientside Script" class="both" show="true">
``` lua
function isVehicleEmpty( vehicle )
    if not isElement( vehicle ) or getElementType( vehicle ) ~= "vehicle" then
        return true
    end

    local passengers = getVehicleMaxPassengers( vehicle )
    if type( passengers ) == 'number' then
        for seat = 0, passengers do
            if getVehicleOccupant( vehicle, seat ) then
                return false
            end
        end
    end
    return true
end
```

</section>
See Also
--------
